<template>
  <div id="app">
    <div class="column is-half is-offset-one-quarter">
    <div v-for="(poke,index) in pokemons" :key="index">
      <pokemon :name="poke.name" :url="poke.url" :num="index+1" />
    </div>
    </div>


  </div>
</template>

<script>
import axios from "axios";
import Pokemon from './components/Pokemon.vue';
export default {
  name: 'App',
  data(){
    return {
      pokemons: []
    }
  },
  created: function(){
  axios.get("https://pokeapi.co/api/v2/pokemon?limit=153&offset=251").then(res => {
      this.pokemons = res.data.results;
    })
  },
  components: {
    Pokemon
  }

}
</script>

<style>

</style>
