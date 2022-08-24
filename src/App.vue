<template>
  <div class="bg-blue-400 px-10 h-screen flex flex-col justify-center">
    
    <HelloWorld msg="Welcome to Your Vue.js + TypeScript App"/>
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import HelloWorld from './components/HelloWorld.vue';
// import ChampionsGallery from './components/ChampionsGallery.vue'

export default defineComponent({
  name: 'App',
  components: {
    HelloWorld,

  }
});
</script>

<style>

</style>
