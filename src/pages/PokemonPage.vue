<template>
  <div class="container">
    <div class="loading" v-if="!pokemon">
      <h1>Espere por favor...</h1>
    </div>
    <div v-else>
      <h1>¿Quién es este pokémon?</h1>
      <PokemonImage :pokemonId="pokemon.id" :showPokemon="showPokemon" />
      <PokemonOptions :pokemons="pokemonArr" @selection="respAnwser" />
      <div class="points">
        <h2>Tu Puntaje: {{ count }}</h2>
        <button @click="count = 0">Volver a cero</button>
      </div>
      <div class="container-message" v-if="showAnswer">
        <h2 class="fade-in">{{ message }}</h2>
        <button class="btnPokemonPage" @click="newGame">Nuevo Juego</button>
      </div>
    </div>
  </div>
</template>

<script>
import PokemonImage from "@/components/PokemonImage.vue";
import PokemonOptions from "@/components/PokemonOptions.vue";
import getPokemonOptions from "@/helpers/getPokemonOptions";

export default {
  components: { PokemonImage, PokemonOptions },
  data() {
    return {
      pokemonArr: [],
      pokemon: null,
      showPokemon: false,
      showAnswer: false,
      message: "",
      count: 0
    };
  },
  methods: {
    async mixPokemonArray() {
      this.pokemonArr = await getPokemonOptions();

      const rndInt = Math.floor(Math.random() * 4);
      this.pokemon = this.pokemonArr[rndInt];
    },
    respAnwser(selectedId) {
      this.showPokemon = true;
      this.showAnswer = true;

      if (selectedId === this.pokemon.id) { 
        this.message = `Correcto, ${this.pokemon.name.toUpperCase()}`;
        this.count += 1;
      } else {
        this.message = `Oops, era ${this.pokemon.name.toUpperCase()}`;
      }
    },
    newGame() {
      this.showPokemon = false;
      this.showAnswer = false;
      this.pokemonArr = [];
      this.pokemon = null;
      this.mixPokemonArray();
    },
  },
  mounted() {
    this.mixPokemonArray();
  },
};
</script>

<style scoped>
@import "../css/PokemonPage.css";
@import "@/css/normalize.css";
</style>
