<template>
  <div class="pokemon">
    <img class="pokemonImg" :src="pokemonsData.sprites.shiny" alt="" />
    <span class="pokemonName">
      {{ pokemonsData.name }}
    </span>
  </div>
</template>

<script>
export default {
  name: 'PokemonCard',
  props: {
    url: String,
  },
  data() {
    return {
      pokemonsData: [],
    };
  },
  methods: {
    async getPokemonData() {
      const response = await fetch(this.url);
      const data = await response.json();
      this.pokemonsData = data;

      console.log('data', data);
    },
  },
  mounted() {
    this.getPokemonData();
  },
};
</script>

<style scope>
.pokemon {
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
