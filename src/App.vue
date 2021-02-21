<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <Game />
  </div>
</template>

<script>
import Game from './components/Game.vue'

export default {
  name: 'App',
  components: {
    Game
  }
}
</script>

<style scoped>
img {
  width: auto;
  height: 60px;
}
</style>

