<template>
  <section class="pokemon-container">
    <ul class="pokemon-list">
      <li v-for="pokemon in pokemons" :key="pokemon.name" class="pokemon-card">
        <PokemonCard :url="pokemon.url" />
      </li>
    </ul>
  </section>
</template>

<script>
import PokemonCard from './PokemonCard.vue';
export default {
  name: 'PokemonContainer',
  props: {
    pokemons: Array,
  },
  components: {
    PokemonCard,
  },
};
</script>
<style scoped>
.pokemon-container {
  width: 100%;
  height: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: row;
  flex-wrap: wrap;
}
.pokemon-list {
  width: 100%;
  height: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: row;
  flex-wrap: wrap;
  padding: 10px;
  border: 1px solid #000;
}
.pokemon-card {
  width: 175px;
  height: 250px;
  list-style: none;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  flex-wrap: wrap;
}
</style>
