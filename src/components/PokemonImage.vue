<template>
  <div class="pokemon-container">
    <img :src="imgSrc"
    class="hidden-pokemon"
    alt="pokemon">

<img v-if="showPokemon"
  class="fade-in"
  :src="imgSrc"
  alt="pokemon">
  </div> 
</template>

<script>
export default {
  props: {
    pokemonId: {
      type: Number,
      required: true
    },
    showPokemon: {
      type: Boolean,
      required: true,
      default: false
    }  
  },
  computed:{
    imgSrc() {
    return `https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/other/dream-world/${this.pokemonId}.svg`
  }
  },  
}
</script>

<style scoped>
@import '../css/PokemonImage.css';
</style>
  
