<script setup>
    import Home from "./components/Home.vue";
    import VueCookies from 'vue-cookies';
    import modal from "./components/modal.vue"
</script>

<template>
  <modal v-if="modalOpen" @close = "modalOpen = false"/>
  <Home/>
</template>

<script>
  export default {
    name: "App",
    data(){
      return {
        modalOpen: true
      }
    },
    methods: {

    }
  }

</script>

<style scoped>


</style>
