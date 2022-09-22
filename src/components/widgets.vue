<script setup>
    import weather from "@/components/weather.vue"
    import news from "@/components/news.vue"
    import toDo from "@/components/toDo.vue"
</script>

<template>
    <div class="wrapper">
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
    }
</style>
