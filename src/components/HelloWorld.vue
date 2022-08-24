<template>
  <div class="hello">
  <!-- {{selecionado}} -->
  <champions-gallery @click="teste"></champions-gallery>
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import ChampionsGallery from './ChampionsGallery.vue';

export default defineComponent({
  name: 'HelloWorld',
  props: {
    msg: String,
  },
  data(){
    return{
      // selecionado: 'ddd',
    }
  },
  components:{
    ChampionsGallery
  },
//   methods: {
// 		teste(index: unknown) {
// 			// console.log("teste selecionado", index);
// 		},
//     }
});
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
