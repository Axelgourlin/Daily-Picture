<template>
  <div>
    <div id="nav">
      <router-link to="/">Home</router-link> |
      <router-link to="/about">About</router-link>
    </div>
    <router-view class="container mx-auto w-screen" />
  </div>
</template>

<script lang="js">
import "./assets/tailwind.css";
export default {
}
</script>

<style>
#app {
  font-family: "Poppins", sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: rgb(201, 201, 201);
  background-color: #2c3e50;
}

#nav {
  padding: 15px;
}

#nav a {
  font-weight: bold;
  color: rgb(201, 201, 201);
}

#nav a.router-link-exact-active {
  color: #b36eec;
}
</style>
