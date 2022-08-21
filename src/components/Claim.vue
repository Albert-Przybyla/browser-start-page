<script setup>
import VueWriter from 'vue-writer'
</script>


<template>
    <div class="wrapper">
         <VueWriter :array="['Hello World']" />
    </div>
</template>

<script>
    export default {
    name: "Clime",
    components: {
        VueWriter
    },
    data(){
        return {
                
        }
    },

}
</script>



<style scoped>


</style>