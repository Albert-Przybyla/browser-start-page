<template>
    {{item.title}}
</template>

<script>
    export default {
        name: "newsItem",
        props: {
            item:{
                type: Object,
                required: true,
            },

        },
        computed: {
          style () {
            return 'background-image: url(' +  this.item[index].relToImage + ');'
          }
        },
    
    
        }
</script>

<style scoped>

</style>