<template>
  <div>
    <poke-display
      v-for="pokemon in pokemons"
      :key="pokemon"
      :pokemon="pokemon"
    />
  </div>
</template>

<script>
import PokeDisplay from "./components/PokeDisplay.vue";
import axios from "axios";

export default {
  name: "App",
  components: {
    PokeDisplay,
  },
  data() {
    return {
      pokemons: [],
    };
  },
  methods: {
    async getPokemons() {
      try {
        const url = "https://pokeapi.co/api/v2/pokemon/?limit=20";
        const response = await axios.get(url);
        this.pokemons = response.data.results;
        console.log(this.pokemons);
      } catch (error) {
        console.error(error);
      }
    },
  },
  mounted() {
    this.getPokemons();
  },
};
</script>

<style></style>
