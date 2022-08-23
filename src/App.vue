<script setup>
    import Home from "./components/Home.vue";
    import VueCookies from 'vue-cookies';
    import modal from "./components/modal.vue"
</script>

<template>
  <modal v-if="modalOpen" @close = "modalOpen = false" @update:option="optionUpdate"/>
  <Home :bg = "bg" @openModal = "modalOpen = true"/>
</template>

<script>
  export default {
    name: "App",
    data(){
      return {
        modalOpen: true,
        bg: 1,
      }
    },
    methods: {
      optionUpdate: function(value){
        this.bg = value
      }
    }
  }

</script>

<style scoped>


</style>
