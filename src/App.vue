<template>
  <div id="app">
    <AddressInfo/>
  </div>
</template>

<script>
import AddressInfo from './components/AddressInfo.vue'

export default {
  name: 'App',
  components: {
    AddressInfo,
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
