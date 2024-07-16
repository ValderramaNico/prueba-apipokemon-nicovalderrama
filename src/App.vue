<template>
  <div>
    <HeaderSection />
  </div>
  <div>
    <h3>
      Pokemones descubiertos:
      <p class="count">{{ pokemonDiscoveredCount }}</p>
    </h3>
  </div>
  <div class="pokemonCard">
    <poke-display
      v-for="pokemon in pokemons"
      :key="pokemon"
      :pokemon="pokemon"
      @pokemon-discovered="discoveredCount"
    />
  </div>
</template>

<script>
import HeaderSection from "./components/HeaderSection.vue";
import PokeDisplay from "./components/PokeDisplay.vue";
import axios from "axios";

export default {
  name: "App",
  components: {
    PokeDisplay,
    HeaderSection,
  },
  data() {
    return {
      pokemons: [],
      pokemonDiscoveredCount: 0,
    };
  },
  methods: {
    async getPokemons() {
      try {
        const randomNumber = Math.ceil(Math.random() * 151);
        const URL_BASE = "https://pokeapi.co/api/v2/pokemon?offset="+randomNumber;
        const responseApi = await axios.get(URL_BASE);
        const primerLlamado = responseApi.data.results;
        console.log(primerLlamado);

        const pokemonResponse = await Promise.all(
          primerLlamado.map(async (pokemon) => {
            const { data } = await axios.get(pokemon.url);
            return data;
          })
        );

        const formattedPokemons = pokemonResponse.map((pokemon) => {
          console.log(pokemon.sprites.other.dream_world);
          const newPokemon = {
            name: pokemon.name,
            image: pokemon.sprites.other.dream_world.front_default,
          };
          return newPokemon;
        });
        this.pokemons = formattedPokemons;
      } catch (error) {
        console.error(error);
      }
    },
    discoveredCount() {
      this.pokemonDiscoveredCount++;
    },
  },
  mounted() {
    this.getPokemons();
  },
};
</script>

<style>
* {
  padding: 0;
  margin: 0;
  box-sizing: border-box;
  font-family: sans-serif;
}

.pokemonCard {
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
  justify-content: space-evenly;
  gap: 1.5rem;
  padding: 4%;
}

h3 {
  margin-top: 2rem;
  display: flex;
  justify-content: center;
  align-items: center;
  gap: 5px;
}

.count {
  font-size: 28px;
  color: #ffcb05;
  font-weight: 800;
  -webkit-text-stroke-width: 2px;
  -webkit-text-stroke-color: #2b73b9;
}
</style>
