<template>
  <div class=api-call-div>
    <SendersRecipients v-bind:inputs="info.inputs" v-bind:outputs="info.outputs"/>
  </div>
</template>

<script>
import SendersRecipients from './SendersRecipients.vue'

export default {
  name: 'AdressInfo',
  props: {
    msg: String
  },
  data () {
    return {
      info: null
    }
  },
  mounted () {
    this.axios
      .get('https://api.blockchair.com/bitcoin/dashboards/transaction/2fa53203c821782d07fad4f435d646656fd9ef024d1374d3a3c4d330575a126b')
      .then((response) => { this.info = response.data.data[Object.keys(response.data.data)] })
  },
  components: {
    SendersRecipients
  }
}
</script>

<style scoped>
</style>