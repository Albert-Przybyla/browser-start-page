<script setup>
    import Home from "./components/Home.vue";
    import modal from "./components/modal.vue";
    import widgets from "./components/widgets.vue";
</script>

<template>
  <modal v-if="modalOpen" @close = "modalOpen = false" @update:option="optionUpdate"/>
  <Home :bg = "bg" @openModal = "modalOpen = true"/>
  <widgets/>
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
    components: {
        Home, 
        modal, 
        widgets,
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
