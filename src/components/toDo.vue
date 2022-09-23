<script setup>

</script>

<template>
    <div class="toDoBox">
        <div class="menu" :class="{ closeMenu: !menu}">
            <div class="add" v-if="!menu" @click="add">+</div>
            <div class="menuShow" v-else>
                <input 
                type="text"
                placeholder="type something and press enter">
                <button @click="add">
                    or cancel 
                </button>
            </div>
            
        </div>
    </div>
</template>

<script>
export default {
    name: "toDo",
    components: {

    },
    data() {
        return {
            menu: false,

        }
    },
    methods: {  
        add(){
            this.menu = !this.menu
        }
    },
    beforeMount(){

    }


    }
</script>

<style scoped>
    .toDoBox{
        margin-top: 5vw;
        width: 90%;
        height: 65vh;
        border-radius: 20px;
        background-color: var(--color-text);
        background-size: cover;
        background-repeat: no-repeat;
        background-position: 50%;
        transition: .4s;
        display: flex;
        flex-direction: column;
    }

    .menu {
        position: absolute;
        right: 0px;
        bottom: 0px;
        background-color: var(--color-background);
        transition: .5s easy;
    }

    .closeMenu{
        border-radius: 100%;
        margin-right: 10px;
        margin-bottom: 10px;
    }

    .add{
        width: 100%;
        height: 100%;
        display: flex;
        justify-content: center;
        align-items: center;
        font-size: 45px;
        width: 30px;
        height: 30px;
        padding: 30px;
        cursor: pointer;
    }

    .menuShow{
        width: 90vw;
        height: 15vh;
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: space-around;
    }

    .menuShow input{ 
        background-color: var(--color-background);
        border: none;
        border-bottom: 2px var(--color-text) solid;
        color: var(--color-text);
        width: 90%;
        height: 35%;
        font-size: 18px;
    }

    input:focus{
        outline: none;
    }
    
</style>