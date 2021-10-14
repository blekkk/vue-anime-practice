<template>
  <img alt="Vue logo" src="./assets/logo.png">
  <Animes />
</template>

<script>
import Animes from './components/Animes.vue'

export default {
  name: 'App',
  components: {
    Animes
  }
}
</script>

<style>
:root {
  --main-color: #42b983;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
