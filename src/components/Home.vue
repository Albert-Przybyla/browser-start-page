<script setup>
    import claim from "@/components/Claim.vue"
</script>

<template>
    <header>
    <claim/>
    </header>
</template>

<script>
export default {
  name: "Home",
  data(){
    return {
        components: {claim},
    }
  }
};
</script>

<style scoped>

</style>