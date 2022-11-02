<script>
import axios from "axios";

export default {
  data: function () {
    return {
      message: "Welcome to Norando, where randoms do not exist.",
      posts: [],
      newPostParams: {},
      currentPost: {},
      editPostParams: {},
    };
  },
  created: function () {
    this.indexPosts();
  },
  methods: {
    indexPosts: function () {
      axios.get("/posts.json").then((response) => {
        this.post = response.data;
        console.log("All Posts:", this.posts);
      });
    },
    createPost: function () {
      axios
        .post("/posts.json", this.newPostParams)
        .then((response) => {
          console.log("Success!", response.data);
          this.posts.push(response.data);
        })
        .catch((error) => console.log(error.response));
    },
    showPost: function (post) {
      console.log(post);
      this.currentPost = post;
      this.editPostParams = post;
      document.querySelector("#post-details").showModal();
    },
    updatePost: function (post) {
      axios.patch("/posts/" + post.id + ".json", this.editRecipeParams).then((response) => {
        console.log("Success!", response.data);
      });
    },
    destroyPost: function (post) {
      axios.delete("/posts/" + post.id).then((response) => {
        console.log("Success!", response.data);
        var index = this.posts.indexOf(post);
        this.posts.splice(index, 1);
      });
    },
  },
};
</script>

<template>
  <div class="home">
    <h1>{{ message }}</h1>
    <h2>Find friends to play games with!</h2>
    <h3><router-link to="/games">View all games</router-link></h3>
  </div>
</template>

<style></style>
