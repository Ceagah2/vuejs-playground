<template>
  <main class="container">
    <PokeHeader />
    <PokemonContainer :pokemons="pokemons" />
  </main>
</template>

<script>
import PokeHeader from './components/Header.vue';
import PokemonContainer from './components/PokemonContainer.vue';

export default {
  name: 'App',
  components: {
    PokeHeader,
    PokemonContainer,
  },
  data() {
    return {
      pokemons: [],
    };
  },
  methods: {
    async getPokemons() {
      try {
        const response = await fetch('https://pokeapi.co/api/v2/pokemon');
        const data = await response.json();
        console.log(data.results);
        this.pokemons = data.results;
      } catch (error) {
        console.error('Error fetching pokemons:', error);
      }
    },
  },
  mounted() {
    this.getPokemons();
  },
};
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
.container {
  width: 100%;
  min-height: 100vh;
  height: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
}
.pokemon-container {
  width: 100%;
  min-height: 100vh;
  height: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  flex-wrap: wrap;
  gap: 20px;
  padding: 20px;
}
</style>
