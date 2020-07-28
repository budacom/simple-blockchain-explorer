<template>
  <div>
      <div class="container">
            <div class="select-container">
              <select class="select-coin"
                v-model="message"
              >
                <option
                  disabled
                  value=""
                >
                  Select Coin
                </option>
                <option
                  v-for="coin in coins"
                  :value="coin"
                  :key="coin"
                >
                  {{ coin }}
                </option>
              </select>
            </div>
        <div clas="text-container">
          <input class="hash-input" v-model="hash" placeholder="hash">
          <button
                  type="button"
                  class="btn"
                  @click="getTx"
                >
                  Buscar
          </button>
        </div>
      </div>
      <div clas="results-container">
        <div v-for="(value, name) in list" :key="name">
          {{ name }}: {{ value }}
        </div>
        <SendersRecipients v-if="apiResponse" v-bind:inputs="inputs" v-bind:outputs="outputs"/>
      </div>
  </div>
</template>

<script>

import SendersRecipients from './SendersRecipients.vue'

export default {
    data() {
    return {
      message:'btc',
      hash:'',
      apiResponse: null,
      list: {},
      coins: ['btc', 'ltc'],
      inputs: [],
      outputs: [],
    };
  },
  components: {
    SendersRecipients,
  },
  methods: {
    getTx() {
      this.axios
      .get(` https://api.blockcypher.com/v1/${this.message}/main/txs/${this.hash}`)
      .then((response) => {
        this.apiResponse = response.data
        if (this.apiResponse) {
          this.list["comisiones"] = `${this.apiResponse.fees/100000000} ${this.message}`
          this.list["monto"] = `${this.apiResponse.total} ${this.message}`
          this.list["confirmaciones"] = `${this.apiResponse.confirmations}`
          this.inputs = this.apiResponse.inputs
          this.outputs = this.apiResponse.outputs
        }
        })
  },
    },
  mounted() {
  },
}
</script>

<style scoped>
.container {
  display: flex;
  justify-content: space-between;
  padding-left: 500px;
  padding-right: 350px;
}

.select-coin {
  height: 40px;
  width: 150px;
  font-size: 30px;
  font-family: sans-serif;
  border-radius: 8px;
}

.select-container {
  padding-top: 15px;
}

.hash-input {
  height: 35px;
  width: 200px;
  font-size: 30px;
  font-family: sans-serif;
  border-radius: 8px;
}

.btn {
  height: 40px;
  width: 120px;
  font-size: 30px;
  font-family: sans-serif;
  padding:0.6em 2em;
  border-radius: 8px;
  color:#fff;
  background-color:#1976d2;
  font-size:1.1em;
  border:0;
  cursor:pointer;
  margin:1em;
}
</style>