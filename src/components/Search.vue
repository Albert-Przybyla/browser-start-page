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
        justify-content: center;
        align-items: center;
        width: 90%;
        height: 20vh;
    }

    .weatherBox .search{
        width: 100%;
        height: 15vh;
    }

    .weatherBox .search input{
        width: 250px;
        height: 40px;
        font-size: 25px;
    }

    .weatherBox .search span{
        width: 40px;
        height: 40px;
    }

    input{
        height: 50px;
        width: 300px;
        border: none;
        background-color:  var(--color-background);
        border-top-right-radius: 15px;
        border-bottom-right-radius: 15px;
        font-size: 30px;
        color: var(--color-text);
    }

    span{
        background: var(--color-background);
        height: 50px;
        width: 50px;
        display: flex;
        justify-content: center;
        align-items: center;
        border-top-left-radius: 15px;
        border-bottom-left-radius: 15px;
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

    @media (min-width: 760px){
        input{
            width: 350px;
            height: 60px;
        }

        span{
            width: 60px;
            height: 60px;
        }
    }

    @media (min-width: 1024px){
        input{
            width: 400px;
            height: 65px;
        }

        span{
            width: 65px;
            height: 65px;
        }
    }

    @media (min-width: 2524px){
        input{
            width: 600px;
            height: 75px;
        }

        span{
            width: 75px;
            height: 75px;
        }
    }
    

</style>