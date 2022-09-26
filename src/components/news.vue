<script setup>
    import axios from 'axios';
</script>

<!-- v-show="active==index" -->

<template>
    <div class="newsBox">
        <div class="item" v-for="(item, index) in items" :key="item" :class="{left: active>index, right: active<index, active: active === index}">
                <img :src="item.urlToImage" alt="">
                <div class="content">
                        <h3>
                            {{item.title}}
                        </h3>
                        <p>
                            {{item.content}}
                        </p>
                        <i> 
                            ~ {{item.author}}
                        </i>
                        
                        <a :href="item.url">full article available here</a>
                </div>
        </div>
        <span class="material-symbols-outlined back double" @click="changeNews(-1)" v-if="firstSlide">
            keyboard_double_arrow_right
        </span>
        <span class="material-symbols-outlined back" @click="changeNews(-1)" v-else>
            arrow_back_ios
        </span>
        <span class="curentSlide"><sup>{{active+1}}</sup>/<sub>20</sub></span>
        <span class="material-symbols-outlined forward double" @click="changeNews(1)" v-if="lastSlide">
            keyboard_double_arrow_left
        </span>
        <span class="material-symbols-outlined forward" @click="changeNews(1)" v-else>
            arrow_forward_ios
        </span>
    </div>
</template>

<script>
export default {
    name: "news",
    components: {
       
    },
    data() {
        return {
            api: 'https://newsapi.org/v2/top-headlines?country=us&apiKey=06dbaa83a995486db090deed0040045d',
            items: [],
            active: 0,
            firstSlide: true,
            lastSlide: false,
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
            this.lastSlide = false
            this.firstSlide = false
                if(this.active==19){
                    this.lastSlide = true
                }
                if(this.active==0){
                    this.firstSlide = true
                }
            }else if(add == -1){
                this.active = 19
                this.lastSlide = true
                this.firstSlide = false
            }else{
                this.active = 0
                this.firstSlide = true
                this.lastSlide = false
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
        height: 70vh;
        border-radius: 20px;
        background-color: var(--color-background);
        /* background-image: url(../assets/newspaper.jpeg);
        background-size: cover;
        background-repeat: no-repeat; */
        background-position: 50%;
        transition: .4s;
        color: black;
        overflow: hidden;
    }

    .left{
        transform: translateX(-100vw);
        transition: .5s;
    }

    .right{
        transform: translateX(100vw);
        transition: .5s;
    }

    .active{
        transform: translateX(0);
        transition: .5s;
    }

    .item{
        width: 100%;
        height: 100%;
        position: absolute;
        top: 0;
        left: 0;
        overflow: hidden;
    }

    .item img{
        position: absolute;
        top: 0;
        left: 0;
        height: 70%;
        z-index: 1;
    }

    .content{
        position: absolute;
        top: 0;
        left: 0;
        height: 85%;
        width: 100%;
        z-index: 2;
        background-color: rgba(0, 0, 0, 0.5);
        color: white;
    }

    .content a{
        text-decoration: none;
        color: white;
        position: absolute;
        left: 0;
        bottom: 0;
        width: 100%;
        height: 15%;
        display: flex;
        justify-content: center;
        align-items: center;
        font-size: 20px;
    }

    .content h3{
        margin: 8px;
        padding: 10px;
        border-radius: 10px;
        font-size: 18px;
        text-align: center;
        font-weight: 600;
        background-color: rgba(0, 0, 0, 0.6);
    }

    .content p{
        margin: 8px;
        padding: 10px;
        border-radius: 10px;
        margin-top: 30px;
        text-align: justify;
        font-size: 15px;
        background-color: rgba(0, 0, 0, 0.6);
    }

    .content i{
        position: absolute;
        max-width: 90%;
        right: 5%;
        bottom: 18%;
        display: -webkit-box;
        -webkit-line-clamp: 1;
        -webkit-box-orient: vertical;
        overflow: hidden;
    }

    .back{
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

    .forward{
        position: absolute;
        right: 0;
        bottom: 0;
        width: 40%;
        cursor: pointer;
        border-bottom-right-radius: 20px;
    }

    .double{
        font-size: 45px;
    }

    span{
        height: 15%;
        display: flex;
        justify-content: center;
        align-items: center;
        font-size: 30px;
        background-color: rgba(0, 0, 0, 0.5);
        z-index: 3;
        color: white;
    }

    
</style>