<template>
    <div class="options-container">
      <ul>
        <li v-for="pokemon in pokemons"
        :key="pokemon.id"
        @click="$emit('selection', pokemon.id)">
          {{ pokemon.name }}
        </li>
      </ul>

    </div>
  </template>
  
  <script>
  export default {
    props: {
      pokemons: {
        type: Array,
        required: true
      }
    }
  }
  </script>
  
<style scoped>
@import '../css/PokemonOptions.css';
</style>