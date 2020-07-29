<template>
  <div>
      <div class="container">
            <div class="select-container">
              <select class=select-coin v-model="selected_coin">
                <option value='0'>Bitcoin</option>
                <option value='1'>Litecoin</option>
              </select>
            </div>
        <div class="text-container">
          <input class="text-input" v-model="hash" placeholder="Hash">
        </div>
        <div class="button-container">
          <button
            type="button"
            class="search-button"
            @click="getTx"
          >Buscar
          </button>
        </div>
      </div>
      <div class="results-container">
        <p v-for="(value, name) in list" :key="name">
          {{ name }}: {{ value }}
        </p>
        <SendersRecipients v-if="apiResponse" v-bind:inputs="inputs" v-bind:outputs="outputs" :denomination="this.coins[this.selected_coin][1]"/>
      </div>
  </div>
</template>

<script>

import SendersRecipients from './SendersRecipients.vue'

export default {
    data() {
    return {
      selected_coin: 0,
      hash:'',
      apiResponse: null,
      list: {},
      coins: [
        ["btc", "BTC", "Bitcoins", "Satoshi"],
        ["ltc", "LTC", "Litecoins", "Litoshi"]
      ],
      inputs: [],
      outputs: [],
    };
  },
  components: {
    SendersRecipients,
  },
  methods: {
    getTx() {
      this.apiResponse = null
      this.list = {}
      this.axios
      .get(` https://api.blockcypher.com/v1/${this.coins[this.selected_coin][0]}/main/txs/${this.hash}`)
      .then((response) => {
        this.apiResponse = response.data
        if (this.apiResponse) {
          this.list["Monto"] = `${this.apiResponse.total/100000000} ${this.coins[this.selected_coin][1]}`
          this.list["Comisiones"] = `${this.apiResponse.fees/100000000} ${this.coins[this.selected_coin][1]}`
          this.list["Confirmaciones"] = `${this.apiResponse.confirmations}`
          this.inputs = this.apiResponse.inputs
          this.outputs = this.apiResponse.outputs
        }
        })
      .catch(error => {
        if (!error.response || error.response.status != 200) {
          alert("No fue posible acceder a la transacción dada")
        }
      })
  },
    },
  mounted() {
  },
}
</script>

<style scoped>
</style>