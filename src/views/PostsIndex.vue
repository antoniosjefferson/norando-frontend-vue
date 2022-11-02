<script>
import axios from "axios";

export default {
  data: function () {
    return {
      message: "All Posts",
      posts: [],
      users: [],
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
        this.posts = response.data;
        console.log("All Posts:", this.posts);
      });
    },
    // createPost: function () {
    //   axios
    //     .post("/posts.json", this.newPostParams)
    //     .then((response) => {
    //       console.log("Success!", response.data);
    //       this.posts.push(response.data);
    //     })
    //     .catch((error) => console.log(error.response));
    // },
    // showPost: function (post) {
    //   console.log(post);
    //   this.currentPost = post;
    //   this.editPostParams = post;
    //   document.querySelector("#post-details").showModal();
    // },
    // updatePost: function (post) {
    //   axios.patch("/posts/" + post.id + ".json", this.editRecipeParams).then((response) => {
    //     console.log("Success!", response.data);
    //   });
    // },
    // destroyPost: function (post) {
    //   axios.delete("/posts/" + post.id).then((response) => {
    //     console.log("Success!", response.data);
    //     var index = this.posts.indexOf(post);
    //     this.posts.splice(index, 1);
    //   });
    // },
  },
};
</script>

<template>
  <button @click="$router.push('/posts/new')">Create A Post</button>
  <div class="col d-flex justify-content-center">
    <div v-for="post in posts" v-bind:key="post.id" class="card" style="width: 18rem">
      <div class="card-body">
        <h5 class="card-title">{{ post.title }}</h5>
        <h6 class="card-subtitle mb-2 text-muted">{{ post.user_id }}</h6>
        <p class="card-text">
          {{ post.body }}
        </p>
        <!-- <a href="#" class="card-link">Card link</a>
        <a href="#" class="card-link">Another link</a> -->
      </div>
    </div>
    <!-- OLD LOOP
      <div>
      <div class="posts">
        <div v-for="post in posts" v-bind:key="post.id">
          <h2>{{ post.title }}</h2>
          <p>{{ post.body }}</p>
        </div>
      </div>
    </div> -->
  </div>
</template>

<style>
.card {
  align-self: center;
}
</style>
