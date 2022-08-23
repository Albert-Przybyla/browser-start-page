<script setup>
    import claim from "@/components/Claim.vue"
    import search from "@/components/Search.vue"
    import Shortcuts from "@/components/Shortcuts.vue"
</script>

<template>
    <header :style="style">
        <claim/>
        <search/>
        <Shortcuts/>
        <div class="setting">
          <span class="material-symbols-outlined" @click="openModal">
            settings
          </span>
        </div>
    </header>
</template>

<script>
export default {
  name: "Home",
  components: {
    claim,
    search,
    Shortcuts
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
    methods: {
      openModal(){
        this.$emit('openModal')
      }
    }
};
</script>

<style scoped>
    header{
        height: 85vh;
        width: 100vw;
        background-size: cover;
        background-repeat: no-repeat;
        background-position: 50%;
        display: flex;
        flex-direction: column;
        justify-content: space-around;
        align-items: center;
        text-shadow: 2px 2px var(--color-background);
    }

    .setting{
      width: 100%;
      height: 10vh;
      display: flex;
      justify-content: right;
      align-items: flex-end;
    }

    .setting span{
      margin-right: 10%;
      font-size: 40px;
      cursor: pointer;
    }
</style>