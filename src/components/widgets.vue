<script setup>
    import weather from "@/components/weather.vue"
</script>

<template>
    <div class="wrapper">
        <weather/>
    </div>
</template>

<script>
    export default {
    name: "widgets",
    components: {
    weather
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
