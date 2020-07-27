<template>
  <div id="app">
    <AdressInfo/>
  </div>
</template>

<script>
import AdressInfo from './components/AdressInfo.vue'

export default {
  name: 'App',
  components: {
    AdressInfo,
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
