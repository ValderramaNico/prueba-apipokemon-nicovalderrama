<template>
  <div class="pokeCard">
    <div class="incognitoPoke">
      <img :src="pokemon.image" alt="Pokémon Img" :style="pokeBlur" />
    </div>
    <ul v-if="pokemon" class="pokemonName" >
      <li v-if="correctName">
        <h2>{{ pokemon.name }}</h2>
      </li>
      <form class="input" @submit.prevent="checkName" v-if="!correctName">
        <input type="text" v-model="inputName" />
        <button type="submit">Descubrir</button>
      </form>
    </ul>
    <modal :visible="showModal" @close="showModal = false">
      <p  >Nombre incorrecto. <br> Inténtalo de nuevo.</p>
    </modal>
  </div>
</template>

<script>
import modal from "./ModalPop.vue";

export default {
  name: "PokeDisplay",
  props: {
    pokemon: {},
  },
  data() {
    return {
      inputName: "",
      correctName: false,
      showModal: false,
    };
  },
  computed: {
    pokeBlur() {
      return this.correctName
        ? {}
        : { filter: ' brightness(0%)' };
    },
  },
  methods: {
    checkName() {
      const lowercaseInputName = this.inputName.toLowerCase();
      const PokemonName = this.pokemon.name;
      if (lowercaseInputName === PokemonName) {
        this.correctName = true;
        this.$emit('pokemon-discovered');
      } else {
        this.showModal = true;
      }
    },
  },
  components: {
    modal,
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

.pokeCard {
  position: relative;
}

.incognitoPoke {
  background-image: url("https://miro.medium.com/v2/resize:fit:1400/1*kZW4nlRSLAMq0EA2EoKStg.png");
  background-size: cover;
  background-repeat: no-repeat;
  width: 360px;
  height: 220px;
  display: flex;
  margin-bottom: 1rem;
  border-radius: 15px;
  position: relative;

}

.input {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  margin-top: 20px;
  row-gap: 0.5rem;
}

.pokemonName {
  display: flex;
  justify-content: center;
}

img {
  width: 160px;
  height: 130px;
  position: absolute;
  left: 35px;
  top: 55px;
}

ul {
  list-style: none;
}

button {
  width: 150px;
  height: 25px;
}

input {
  width: 180px;
  height: 25px;
}
</style>
