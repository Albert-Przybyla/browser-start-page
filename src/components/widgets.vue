<script setup>
    import weather from "@/components/weather.vue"
    import news from "@/components/news.vue"
    import toDo from "@/components/toDo.vue"
</script>

<template>
    <Transition>
        <span class="material-symbols-outlined" v-if="widgetsMove">
            expand_more
        </span>
    </Transition>
    <div class="wrapper" :class="{widgetsMove: widgetsMove}">
        <weather/>
        <news/>
        <toDo/>
    </div>
</template>

<script>
    export default {
    name: "widgets",
    components: {
    weather,
    news,
    toDo
    },
    props: ['widgetsMove'],
    data() {
        return {
        }
    }

    }
</script>

<style scoped>
    .wrapper{
        width: 100%;
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: space-around;
        padding-top: 5vw;
        transition: .6s;
        transition-delay: .1s;
    }

    .widgetsMove{
        transform: translateY(40vh);
        transition: .6s;
    }

    span{
        position: absolute;
        left: 0;
        top: 4vh;
        width: 100%;
        text-align: center;
        font-size: 70px;
        cursor: pointer;
    }

    .v-enter-active, .v-leave-active {
        transition: opacity 0.4s ease;
    }

    .v-enter-from, .v-leave-to {
        opacity: 0;
    }
</style>
