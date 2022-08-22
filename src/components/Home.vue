<script setup>
    import claim from "@/components/Claim.vue"
    import search from "@/components/Search.vue"
</script>

<template>
    <header :style="style">
        <claim/>
        <search/>
    </header>
</template>

<script>
export default {
  name: "Home",
  components: {
    claim,
    search
    },
    props: ['bg'],

  data(){
    return {

    }
  },
   computed: {
      style () {
        return 'background-image: url(src/assets/' +  this.bg + '.jpg);'
      }
    },
};
</script>

<style scoped>
    header{
        height: 85vh;
        width: 100%;
        background-size: cover;
        background-repeat: no-repeat;
        background-position: 50%;
        display: flex;
        flex-direction: column;
        justify-content: space-around;
        align-items: center;
    }
</style>