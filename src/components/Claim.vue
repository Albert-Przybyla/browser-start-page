<script setup>
import axios from 'axios';
import VueWriter from 'vue-writer';
</script>


<template>
    <div class="wrapper">
         <VueWriter :array="greetings" :eraseSpeed="50" :typeSpeed="80" :delay="1500"/>
    </div>
</template>

<script>
    export default {
    name: "Claime",
    components: {
        VueWriter
    },
    data(){
        return {
            greetings: ["hello"],
        }
    },
    methods: {
        show(){
          axios.get(`https://www.greetingsapi.com/greetings`)
              .then((response) => {
                    this.greetings = response.data.greetings
              })
              .catch((error) => {
                  console.log(error)
              })      
        },
    },
    beforeMount(){
        this.show()
    }

}
</script>



<style scoped>
    .wrapper{
        /* width: 80%;
        height: 15vh;
        background: var(--color-background); */
        display: flex;
        justify-content: center;
        align-items: center;
        font-size: 40px;
        font-weight: bold;
        color: var(--color-heading);
    }

</style>