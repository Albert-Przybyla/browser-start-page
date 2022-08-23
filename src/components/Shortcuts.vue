<script setup>
import Modal from '@/components/ModalShortcutAdd.vue'
</script>

<template>
<div class="wrapper">
  <modal v-if="modalOpen" @close = "modalOpen = false"/>
    <div class="shortcut" @click="modalOpen = true">
        <span class="material-symbols-outlined">
          add_circle
        </span>
          add
    </div>
</div>
</template>

<script>
export default {
  name: "Shortcuts",
  data(){
    return {
      modalOpen: false,
    }
  },

};
</script>

<style scoped>


    .material-symbols-outlined {
    font-variation-settings:
    'FILL' 0,
    'wght' 700,
    'GRAD' 0,
    'opsz' 48,
    }

    .shortcut{
      width: 100px;
      height: 150px;
      background: var(--color-background);
      display: flex;
      flex-direction: column;
      justify-content: space-around;
      align-items: center;
      border-radius: 15px;
      border: var(--color-heading) solid 3px;
      cursor: pointer;
    }

    .shortcut span{
      font-size: 50px;
    }

    @media (min-width: 760px){

    }

    @media (min-width: 1024px){

    }

    @media (min-width: 2524px){

    }
    

</style>