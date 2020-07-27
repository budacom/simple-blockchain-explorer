<template>
  <div>
    <p>{{ info }}</p>
  </div>    
</template>

<script>
import Vue from 'vue'
import axios from 'axios'
import VueAxios from 'vue-axios'
Vue.use(VueAxios, axios)

export default {
  name: 'ApiCall',
  props: {
    msg: String
  },
  data () {
    return {
      info: null
    }
  },
  mounted () {
    axios
      .get('https://api.blockchair.com/bitcoin/dashboards/transaction/2fa53203c821782d07fad4f435d646656fd9ef024d1374d3a3c4d330575a126b')
      .then((response) => {console.log(this.info = response)})
  }
}
</script>

<style scoped>
</style>