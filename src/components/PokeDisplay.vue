<template>
  <div class="pokeFeed">
    <ul>
      <div class="whoPoke">
        <img src="" alt="" />
      </div>
      <ul v-if="pokemon">
        <li>{{ pokemon.name }}</li>

      </ul>
    </ul>
  </div>
</template>

<script>
export default {
  name: "PokeDisplay",
  props: {
    pokemon: {
      type: Object,
      required: true,
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.pokeFeed {
  display: grid;
  grid-row: auto
}

.whoPoke {
  background-image: url("https://miro.medium.com/v2/resize:fit:1400/1*kZW4nlRSLAMq0EA2EoKStg.png");
  background-size: cover;
  background-repeat: no-repeat;
  width: 360px;
  height: 220px;
  display: flex;
}
</style>
