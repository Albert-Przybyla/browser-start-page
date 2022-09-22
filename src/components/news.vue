<script setup>
    import axios from 'axios';
    import newsItem from '@/components/newsItem.vue'
</script>

<!-- v-show="active==index" -->

<template>
    <div class="newsBox">
        <newsItem class="item" v-for="(item, index) in items" :key="item" :item = "item" :active = "active" :index = "index"/>
        <span class="material-symbols-outlined" id="back" @click="changeNews(-1)">
            arrow_back_ios
        </span>
        <span class="curentSlide"><sup>{{active+1}}</sup>/<sub>20</sub></span>
        <span class="material-symbols-outlined" id="forward" @click="changeNews(1)">
            arrow_forward_ios
        </span>
    </div>
</template>

<script>
export default {
    name: "news",
    components: {
        newsItem
    },
    data() {
        return {
            api: 'https://newsapi.org/v2/top-headlines?country=us&apiKey=06dbaa83a995486db090deed0040045d',
            items: [],
            active: 0,
        }
    },
    methods: {
        loadNews(){
            axios.get(`${this.api}`)
                .then((response) => {
                    console.log(response.data.articles)
                    this.items = response.data.articles
                })
                .catch((error) => {
                    console.log(error)
                })
        },
        changeNews(add){
            if(add == -1 && this.active >= 1 || add == 1 && this.active <= 18){
            this.active += add

            }
        }
    },
    beforeMount(){
        this.loadNews()
    },

    }
</script>

<style scoped>
    .newsBox{
        margin-top: 5vw;
        width: 90%;
        height: 80vh;
        border-radius: 20px;
        background-color: var(--color-text);
        /* background-image: url(../assets/newspaper.jpeg);
        background-size: cover;
        background-repeat: no-repeat; */
        background-position: 50%;
        transition: .4s;
        color: black;
        overflow: hidden;
    }

    .item{
        width: 100%;
        height: 100%;
        display: inline-block;
    }

    #back{
        position: absolute;
        left: 0;
        bottom: 0;
        width: 40%;
        cursor: pointer;
        border-bottom-left-radius: 20px;
    }

    .curentSlide{
        width: 20%;
        position: absolute;
        left: 40%;
        bottom: 0;
    }

    #forward{
        position: absolute;
        right: 0;
        bottom: 0;
        width: 40%;
        cursor: pointer;
        border-bottom-right-radius: 20px;
    }

    span{
        height: 10%;
        display: flex;
        justify-content: center;
        align-items: center;
        font-size: 30px;
        background-color: rgba(0, 0, 0, 0.5);
        z-index: 2;
    }

    
</style>