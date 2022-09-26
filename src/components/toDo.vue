<script setup>
import { objectToString } from '@vue/shared';


</script>

<template>
    <div class="toDoBox">
        <div class="task" v-for="(task, i) in tasks" :key="task.id" :class="{delete: !task.active, deleted: task.deleted }">
            <span class="material-symbols-outlined" @click="complitedTask(i)" v-if="!task.complited">
                check_box_outline_blank
            </span>
            <span class="material-symbols-outlined" @click="complitedTask(i)" v-else>
                check_box
            </span>

            <p :class="{complited: task.complited}">{{task.name}}</p>
            <span class="material-symbols-outlined" @click="deleteTask(i)">
                delete
            </span>

        </div>
        <div class="menu" :class="{ closeMenu: !menu}">
            <div class="add" v-if="!menu" @click="add">+</div>
            <div class="menuShow" v-else>
                <input 
                type="text"
                v-model="input"
                @keypress="addToDo"
                placeholder="type something and press enter"
                maxlength="20">
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
            input: '',
            tasks:[],
            i: 0,
        }
    },
    methods: {  
        add(){
            this.menu = !this.menu
        },
        addToDo(e){
            if(e.key == "Enter"){
                this.add()
                this.tasks.push ({
                    name: this.input,
                    active: true,
                    deleted: false,
                    complited: false
                })
            }
        },
        deleteTask(i){
            this.tasks[i].active = false
            setTimeout(()=>{
                return this.tasks[i].deleted = true}, 510)
        },
        complitedTask(i){
            this.tasks[i].complited = !this.tasks[i].complited
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
        min-height: 65vh;
        border-radius: 20px;
        background-color: rgb(191, 157, 4);
        background-size: cover;
        background-repeat: no-repeat;
        background-position: 50%;
        transition: .4s;
        display: flex;
        flex-direction: column;
        align-items: center;
        padding: 5%;
        padding-bottom: 90px;
        overflow-x: hidden;
        transition: .5s;
    }

    .task{
        width: 80vw;
        height: 60px;
        background-color: var(--color-background);
        color: var(--color-text);
        padding: 10px;
        display: flex;
        justify-content: space-between;
        align-items: center;
        margin-top: 10px;
        border-radius: 20px;
        transition: .5s;
    }

    .delete{
        transform: translateX(100vw);
    }

    .deleted{
        display: none;
    }

    .complited{
        text-decoration: line-through;
        transition: .5s easy;
    }

    .task span{
        cursor: pointer;
        font-size: 30px;
    }

    .task p{
        max-width: 70%;
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

    .v-enter-active,
    .v-leave-active {
        transition: opacity 0.5s ease;
    }

    .v-enter-from,
    .v-leave-to {
        opacity: 0;
    }
    
</style>