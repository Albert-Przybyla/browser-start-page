<script setup>
import Modal from '@/components/ModalShortcutAdd.vue'
</script>

<template>
<div class="wrapper">
  <transition>
  <modal v-if="modalOpen" @close = "modalOpen = false" @add = "addShortcut"/>
  </transition>
    <div class="shortcut" @click="modalOpen = true">
        <span class="material-symbols-outlined">
          add_circle
        </span>
          add
    </div>
    <a :href="item.link" class="shortcut" v-for="item in shortcuts" :key="item">
      <span>
        {{item.logo}}
      </span>
      {{item.name}}
    </a>
</div>
</template>

<script>
export default {
  name: "Shortcuts",
  data(){
    return {
      modalOpen: false,
      shortcuts: [],
      a: '',
    }
  },
  methods:{
    addShortcut(name, link){
      this.modalOpen = false
      this.shortcuts.push ({
        name: name,
        link: link,
        logo: name.charAt(0)
      })
      console.log(this.shortcuts[0])
    }
  }

};
</script>

<style scoped>
    .wrapper{
      display: flex;
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
      margin: 10px;
      overflow-x: scroll;
      color: var(--color-text);
      text-decoration: none;
    }

    .shortcut .material-symbols-outlined{
      font-size: 50px;
    }

    .shortcut span{
      font-size: 35px;
    }

    @media (min-width: 760px){

    }

    @media (min-width: 1024px){

    }

    @media (min-width: 2524px){

    }
    

</style>