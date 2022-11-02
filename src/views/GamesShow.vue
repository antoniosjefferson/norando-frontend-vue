<script>
import axios from "axios";
export default {
  data: function () {
    return {
      game: {},
      games: [],
    };
  },
  created: function () {
    axios.get("/games/" + this.$route.params.id + ".json").then((response) => {
      this.game = response.data;
      console.log(response.data);
    });
  },
  methods: {},
};
</script>

<template>
  <div>
    <h1>Need friends to play {{ game.title }}?</h1>
    <h2>{{ game.title }}</h2>
    <img :src="game.image_url" alt="Game Image" />
    <p>Released on {{ game.release_date }}</p>
    <p>{{ game.description }}</p>
    <router-link to="/games">Back To All Games</router-link>
  </div>
</template>

<style></style>
