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
  margin-left: 20%;
  margin-right: 20%;
  margin-bottom: 60px;
}
.container {
  display: flex;
  justify-content: space-evenly;
  align-items: flex-start;
}
button {
  font-family: myriad_pro_lightregular,helvetica,arial,sans-serif;
  text-transform: uppercase;
}
.select-container {
  width: 25%;
}

.text-container {
  width: 50%;
}

.button-container {
  width: 25%;
}
.select-coin {
  height: 40px;
  width: 80%;
  margin-right: 20%;
  font-size: 30px;
  font-family: sans-serif;
  border-radius: 8px;
}

.text-input {
  height: 35px;
  width: 90%;
  margin-right: 10%;
  font-size: 30px;
  font-family: sans-serif;
  border-radius: 8px;
  padding-left: 3%;
  padding-right: 3%;
}

.search-button {
  text-align: center;
  height: 40px;
  width: 80%;
  margin-left: 20%;
  font-size: 30px;
  font-family: sans-serif;
  border-radius: 8px;
  color:#fff;
  background-color:#1976d2;
  font-size:1.1em;
  border:0;
  cursor:pointer;
}

.results-container {
  text-align: left;
}
</style>
