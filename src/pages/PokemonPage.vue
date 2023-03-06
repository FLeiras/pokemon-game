<template>
  <h1>¿Quién es este pokémon?</h1>
  <PokemonImage :pokemonId="4" :showPokemon="false" />
  <PokemonOptions />
</template>

<script setup>
import PokemonImage from '@/components/PokemonImage.vue';
import PokemonOptions from '@/components/PokemonOptions.vue';
</script>
