<script setup>

</script>

<template>
    <div class="toDoBox">
        
    </div>
</template>

<script>
export default {
    name: "toDo",
    components: {

    },
    data() {
        return {
            api_key: '0a3bb1ff2db0e040a9982a1d81f55253',
            api_url: 'https://api.openweathermap.org/data/2.5/weather?',
        }
    },
    methods: {

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

    
</style>