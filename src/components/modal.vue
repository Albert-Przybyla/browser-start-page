<script setup>
    import VueCookies from 'vue-cookies';
</script>

<template>
    <div class="backdrop">
        <div class="modal">
                <p>chose background foto:</p>
                <div class="fotobox">
                    <img src="../assets/1.jpg" alt="" @click="choseFoto(1)">
                    <img src="../assets/2.jpg" alt="" @click="choseFoto(2)">
                    <img src="../assets/3.jpg" alt="" @click="choseFoto(3)">
                    <img src="../assets/4.jpg" alt="" @click="choseFoto(4)">
                    <img src="../assets/5.jpg" alt="" @click="choseFoto(5)">
                </div>

           <div class="close" @click="closeModal">

           </div>
        </div>
    </div>
</template>

<script>
    export default {
    name: "App",
    data(){
        return{
            j: ".jpg",
            p: "../assets/",
            active: 1
        }
    },
    methods: {
        closeModal(){
            this.$emit('close');
        },
        choseFoto(number){
            this.$emit('update:option', number);
            this.active = number

        }
    },
    beforeMount(){
        if(false){
        this.choseFoto(1)
        }
    }

    }
</script>


<style scoped>

    .backdrop{
        width: 100%;
        height: 100%;
        position: fixed;
        top: 0;
        left: 0;
        z-index: 5;
    }

    .modal{
        width: 100%;
        height: 100%;
        padding: 50px;
        justify-content: center;
        align-items: center;
        background-color: var(--color-background);
        overflow: scroll;
        border-radius: 20px;
    }

    .fotobox{
        width: 100%;
        display: flex;
        flex-direction: column;
        justify-content: space-around;
        align-items: center;
    }

    .fotobox img{
        margin-top: 5vh;
        width: 80%;
        height: 20vh;
        border-radius: 15px;
        cursor: pointer;
    }

    p{
        font-size: 20px;
        height: 5vh;
        width: 100%;
        text-align: center;
    }


    .close {
        position: absolute;
        width: 30px;
        height: 30px;
        padding: 30px;
        right: 0;
        top: 0;
        cursor: pointer;
    }

    .close::before, .close::after {
            position: absolute;
            top: 30px;
            right: 20px;
            content: '';
            width: 20px;
            height: 2px;
            background: var(--color-text);
            display: block;
}
    .close::before{
        transform: rotate(45deg);
    }

    .close::after{
        transform: rotate(-45deg);
    }

    .border{
        border: blue 3px solid
    }


@media (min-width: 1024px){
    .modal{
        overflow: hidden;
        width: 70%;
        height: 60%;
        padding: 20px;
        background: var(--color-background);
        box-shadow: 0 30px 30px -10px rgba(0,0,0,0.3);
        display: flex;
        flex-direction: column;
    }

    .backdrop {
        top: 0;
        position: fixed;
        background: rgba(0,0,0,0.3);
        width: 100%;
        height: 100%;
        display: flex;
        justify-content: center;
        align-items: center;
        z-index: 2;
    }

    .fotobox{
        padding: 0;
        height: 50%;
        width: 100%;
        flex-direction: row;
    }

    .fotobox img{
        margin: 0;
        width: 15%;
        height: 10vh;
    }

}
</style>