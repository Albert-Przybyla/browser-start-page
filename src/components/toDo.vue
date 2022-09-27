<script setup>
import { objectToString } from '@vue/shared';


</script>

<template>
    <div class="toDoBox">
        <span class="material-symbols-outlined circleAdd" :class="{close: menu}" @click="add">
            add_circle
            </span>
        <transition>
            <div class="menuShow" v-if="menu">
                <div class="title">
                    add ToDo
                </div>
                <input 
                type="text"
                v-model="input"
                @keypress="addToDo($event, colorChosen)"
                placeholder="type something and press enter"
                maxlength="19"
                >
                <div class="colors">
                <span class="material-symbols-outlined" :class="{chosen: colorChosen == 1}" @click="addToDo($event, 1)">
                    text_fields
                </span>
                <span class="material-symbols-outlined" :class="{chosen: colorChosen == 2}" @click="addToDo($event, 2)">
                    text_fields
                </span>
                <span class="material-symbols-outlined" :class="{chosen: colorChosen == 3}" @click="addToDo($event, 3)">
                    text_fields
                </span>
                </div>
                <button @click="add">
                    cancel 
                </button>
            </div>
        </transition>
        <div class="title">
            Todo list
        </div>
        <div class="task" v-for="(task, i) in tasks" :key="task.id" :class="{delete: !task.active, deleted: task.deleted,  bg: task.color === 1, red: task.color === 2, blue: task.color === 3}">
            <span class="material-symbols-outlined" @click="complitedTask(i)" v-if="!task.complited">
                check_box_outline_blank
            </span>
            <span class="material-symbols-outlined" @click="complitedTask(i)" v-else>
                check_box
            </span>

            <p><span class="line" :class="{complited: task.complited}"></span>{{task.name}}</p>


            <span class="material-symbols-outlined" @click="deleteTask(i)">
                delete
            </span>

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
            colorChosen: 1,
        }
    },
    methods: {  
        add(){
            this.menu = !this.menu
        },
        addToDo(e, color){
            if(e.key == "Enter" || e.buttons == 0){
                this.add()
                this.tasks.push ({
                    name: this.input,
                    active: true,
                    deleted: false,
                    complited: false,
                    color: color
                })
                this.colorChosen = color
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
        padding-top: 80px;
        overflow-x: hidden;
        transition: .5s;
    }

    .task{
        width: 80%;
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
        font-size: 18px;
        z-index: 1;
    }

    .bg{
        background-color: var(--color-background);
    }

    .red{
        background-color: rgb(148, 66, 66);
    }

    .blue{
        background-color: rgb(88, 88, 193);
    }

    .delete{
        transform: translateX(100vw);
    }

    .deleted{
        display: none;
    }

    .line{
        position: absolute;
        top: 50%;
        left: 0;
        width: 0;
        height: 1px;
        background-color: var(--color-text);
        transition: .5s;
    }

    .complited{
        width: 105%;
        transition: .5s;
    }

    .task span{
        cursor: pointer;
        font-size: 30px;
    }

    .task p{
        max-width: 70%;
    }

    .circleAdd{
        position: absolute;
        left: 10px;
        top: 10px;
        font-size: 60px;
        color: var(--color-background);
        cursor: pointer;
        z-index: 3;
        transition: .5s;
    }

    .close{
        transform: rotate(45deg);
        color: var(--color-text);
        transition: .5s;
    }

    .menuShow{
        position: absolute;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: space-around;
        background-color: var(--color-background);
        z-index: 2;
    }

    .menuShow .title{
        color: var(--color-text);
    }

    .menuShow input{ 
        margin-top: 80px;
        background-color: var(--color-background);
        border: none;
        border-bottom: 2px var(--color-text) solid;
        color: var(--color-text);
        width: 90%;
        height: 60px;
        font-size: 18px;
    }

    input:focus{
        outline: none;
    }

    .colors{
        display: flex;
        width: 100%;
        justify-content: space-around;
    }

    .colors span{
        width: 70px;
        height: 70px;
        border-radius: 100%;
        background-color: rgb(148, 66, 66);
        display: flex;
        justify-content: center;
        align-items: center;
        cursor: pointer;
    }

    .colors span:first-child{
        background-color: var(--color-background);
    }

    .colors span:last-child{
        background-color: rgb(88, 88, 193);
    }

    .chosen{
        border: 2px solid var(--color-text)
    }

    .menuShow button{
        width: 70%;
        height: 10%;
        background-color: var(--color-background);
        border: 2px solid var(--color-text);
        border-radius: 15px;
        color: var(--color-text);
        font-size: 20px;
        cursor: pointer;
    }

    .title{
        position: absolute;
        right: 40px;
        top: 15px;
        font-size: 30px;
        color: var(--color-background);
    }



    .v-enter-active,
    .v-leave-active {
        transition: opacity 0.5s ease;
    }

    .v-enter-from,
    .v-leave-to {
        opacity: 0;
    }

    .material-symbols-outlined {
        font-variation-settings:
        'FILL' 1,
        'wght' 400,
        'GRAD' 0,
        'opsz' 48
    }

    @media (min-width: 700px){
        
    }

    @media (min-width: 1024px){
        .toDoBox{
            grid-area: ld;
            width: 38vw;
        }
    }
    
</style>