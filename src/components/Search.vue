<script setup>

</script>

<template>
<div class="search">
    <label>
        <span class="material-symbols-outlined">
            search
        </span>
    </label>
    <input type="text" id="">
</div>
</template>

<script>
export default {
  name: "Search",
  data(){
    return {

    }
  },

};
</script>

<style scoped>

    .search{
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-content: center;
    }

    input{
        height: 50px;
        width: 400px;
        margin: 50px;
        border: none;
        background-color:  var(--color-background);
        border-radius: 15px;
        font-size: 40px;
        color: var(--color-text);
        transition: box-shadow .5s;
        text-align: center;
    }

    span{
        color: var(--color-background);
        font-size: 30px;
    }

    input:focus{
        outline: none;
        /* box-shadow: 5px 5px 20px -8px var(--color-text); */
    }

    .material-symbols-outlined {
    font-variation-settings:
    'FILL' 0,
    'wght' 700,
    'GRAD' 0,
    'opsz' 48,
    }
    

</style>