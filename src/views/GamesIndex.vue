<script>
import axios from "axios";

export default {
  data: function () {
    return {
      message: "All Games",
      games: [],
      id: this.$route.params.id,
    };
  },
  created: function () {
    this.indexGames();
  },
  methods: {
    indexGames: function () {
      axios.get("/games.json").then((response) => {
        this.games = response.data;
        console.log("All Games:", this.games);
      });
    },
    // method to route
    // getGameId() {
    //   return this.$router.push("/games/");
    // },
  },
};
</script>

<template>
  <div v-for="game in games" v-bind:key="game.id" class="card-group">
    <div class="card">
      <img v-bind:src="game.image_url" class="card-img-top" alt="Game Image" />
      <div class="card-body">
        <h5 class="card-title">{{ game.title }}</h5>
        <!-- <p class="card-text">
          {{ game.description }}
        </p> -->
        <router-link :to="{ name: 'games-show', params: { id: game.id } }">More Info</router-link>
      </div>
    </div>
  </div>
</template>

<style>
.image-fit {
  height: 100%;
  width: 100%;
  object-fit: cover;
}
</style>
