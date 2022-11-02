<template>
  <nav>
    <router-link to="/">Home</router-link>
    |
    <router-link to="/games">Games</router-link>
    |
    <router-link to="/posts">Posts</router-link>
    |
    <router-link to="/login">Login</router-link>
    |
    <router-link to="/logout">Logout</router-link>
  </nav>
  <router-view />
</template>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #11b2de;
}

nav {
  padding: 30px;
}

nav a {
  font-weight: bold;
  color: #681c97;
  text-decoration: none;
  padding: 10px;
  border-radius: 4px;
}

nav a.router-link-exact-active {
  color: #11b2de;
  background-color: #681c97;
}
</style>
