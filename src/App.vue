<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <DynamicView/>
  </div>
</template>

<script>
import DynamicView from './components/DynamicView.vue'

export default {
  name: 'App',
  components: {
    DynamicView
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
