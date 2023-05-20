<script>
import { computed } from '@vue/reactivity';
import Navbar from '../components/Navbar.vue';
import PokemonList from '../components/PokemonList.vue';

export default{
  name: 'HomeView',
  components:{
    Navbar,
    PokemonList
},
  data(){
    return{
      offset: 0,
      allPokemons: []
    }
  },
  provide(){
    return {
      allPokemons: computed(() => this.allPokemons)
    }
  },
  beforeMount() {
    const getAllPokemons = async(limit = 50) => {
        const baseURL = 'https://pokeapi.co/api/v2/';
        const res = await fetch(`${baseURL}pokemon?limit=${limit}&offset=${this.offset}`);
        const data = await res.json();
        
        const promises = data.results.map(async(pokemon) => {
          const res = await fetch(pokemon.url);
          const data = await res.json();
          return data;
        })

        const results = await Promise.all(promises);
        this.allPokemons = results;
        console.log("home:", results);
    }

    getAllPokemons();

  }


}
</script>

<template>
  <div>
    <PokemonList />
  </div>
</template>

