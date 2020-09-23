<template>
  <div id="app">
    
    <pokemon></pokemon>
    
  </div>
</template>

<script>
import PokemonComponent from "./components/RickMorty.vue";
//import RickMortyComponent from "./components/RickMorty.vue";
  export default {
    data() {
      return {
        message: 'Hola en vue',
      };
    },
    components:{
      'pokemon':PokemonComponent,
    }
  }
</script>

<style scoped>
  
</style>