<script setup>
    import VueCookies from 'vue-cookies';
</script>

<template>
    <div class="backdrop">
        <div class="modal">
                <h2>add shortcut:</h2>
                <!-- <div class="inner">
                <p>
                    cohose one of this: 
                </p>
                <select>
                    <option>facebook</option>
                    <option>instagram</option>
                    <option>messeger</option>
                    <option>google</option>
                    <optino>mozilla MDN</optino>
                </select>
                </div> -->
                <div class="inner">

                <div class="input">
                    <label>
                        <span class="material-symbols-outlined">
                            title
                        </span>
                    </label>
                    <input type="text" name="" id="" placeholder="np. Google" v-model="name">
                </div>
                <div class="input">
                    <label>
                        <span class="material-symbols-outlined">
                            link
                        </span>
                    </label>
                    <input type="text" name="" id="" placeholder="https://" v-model="link">
                </div>
                <div class="input">
                    <div class="submit" @click="addShortcut">
                        add
                    </div>
                </div>

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
            link: '',
            name: '',
        }
    },
    methods: {
        closeModal(){
            this.$emit('close');
        },
        addShortcut(){
            
            this.$emit('add', this.name, this.link);
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
        display: flex;
        flex-direction: column;
        justify-content: flex-start;
        align-items: center;
        background-color: var(--color-background);
        border-radius: 20px;
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

    .inner{
        display: flex;
        flex-direction: column;
        justify-content: flex-start;
        align-items: center;
        margin-top: 40px;
    }

    select{
        margin-top: 10px;
        border: none;
        background: var(--color-background);
        color: var(--color-text);
        margin-left: 25px;
        font-size: 20px;
    }

    h2{
        font-size: 40px;
        height: 5vh;
        color: var(--color-heading);
        width: 100%;
        text-align: center;
    }

    p{
        font-size: 30px;
        margin-top: 15px;
        height: 5vh;
        width: 100%;
        text-align: center;
    }

    .input{
        display: flex;
        justify-content: center;
        align-items: center;
        margin-top: 20px;
    }

    input{
        height: 40px;
        width: 250px;
        border: none;
        background-color:  var(--color-background);
        margin-top: 30px;
        border-top-right-radius: 15px;
        border-bottom-right-radius: 15px;
        font-size: 15px;
        color: var(--color-text);
        border: var(--color-text) solid 2px;
        border-left: none;
    }

    input:focus{
        outline: none;
        /* box-shadow: 5px 5px 20px -8px var(--color-text); */
    }

    .submit{
        height: 40px;
        width: 290px;
        background-color:  var(--color-background);
        margin-top: 30px;
        border-radius: 15px;
        font-size: 15px;
        color: var(--color-text);
        border: var(--color-text) solid 2px;
        display: flex;
        justify-content: center;
        align-items: center;
        cursor: pointer;
    }

    span{
        background: var(--color-background);
        margin-top: 30px;
        height: 40px;
        width: 40px;
        display: flex;
        justify-content: center;
        align-items: center;
        border-top-left-radius: 15px;
        border-bottom-left-radius: 15px;
        border: var(--color-text) solid 2px;
        border-right: none;
        font-size: 20px;
    }

    @media (min-width: 760px){
        input{
            width: 300px;
            height: 45px;
        }
        span{
            height: 45px;
            width: 45px;
        }

    }


    @media (min-width: 1024px){
    .modal{
        overflow: hidden;
        width: 50%;
        height: 60%;
        padding: 20px;
        background: var(--color-background);
        box-shadow: 0 30px 30px -10px rgba(0,0,0,0.3);
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

    .select{
        flex-direction: row;
    }

    select{
        font-size: 25px;
        margin-bottom: 15px;
    }
    input{
        width: 450px;
        height: 50px;
        font-size: 25px;
    }
    span{
        height: 50px;
        width: 50px;
    }
    .submit{
        width: 500px;
        height: 50px;
        font-size: 25px;
        transition: .5s;
    }

    .submit:hover{
        transform: scale(1.1);
        transition: .5s;
    }


    }

    @media (min-width: 2524px){
    input{
        width: 600px;
        height: 50px;
    }
    span{
        height: 50px;
        width: 50px;
    }
    .submit{
        width: 600px;
        height: 50px;
        font-size: 25px;
    }
    }
</style>