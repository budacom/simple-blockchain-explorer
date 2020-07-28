<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <TxFinder/>
  </div>
</template>

<script>
import TxFinder from './components/TxFinder.vue'

export default {
  name: 'App',
  components: {
    TxFinder
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
