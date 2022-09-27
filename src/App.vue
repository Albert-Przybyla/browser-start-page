<script setup>
    import Home from "./components/Home.vue";
    import modal from "./components/modal.vue";
    import widgets from "./components/widgets.vue";
</script>

<template>
  <transition>
  <modal v-if="modalOpen" @close = "modalOpen = false" @update:option="optionUpdate"/>
  </transition>
  <Home :bg = "bg" @openModal = "modalOpen = true"/>
  <div>
  <widgets :widgetsMove = "widgetsMove"/>
  </div>
</template>

<script>
  export default {
    name: "App",
    data(){
      return {
        modalOpen: true,
        bg: 1,
        widgetsMove: true,
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
      },
      handleScroll(event) {
        if(scrollY>=1){
            this.widgetsMove = false
        }else{
            this.widgetsMove = true
        }
      },
    },
    created() {
      window.addEventListener("scroll", this.handleScroll);
    },
    destroyed() {
      window.removeEventListener("scroll", this.handleScroll);
    },
  }

</script>

<style scoped>


</style>
