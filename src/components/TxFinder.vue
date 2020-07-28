<template>
  <div>
          <select
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
    <input v-model="hash" placeholder="hash">
    <button
            type="button"
            class="btn"
            @click="getTx"
          >
            Search
          </button>
    <div v-for="(value, name) in list" :key="name">
      {{ name }}: {{ value }}
    </div>
    <SendersRecipients v-bind:inputs="inputs" v-bind:outputs="outputs"/>
  </div>
</template>

<script>

import SendersRecipients from './SendersRecipients.vue'

export default {
    data() {
    return {
      message:'bitcoin',
      hash:'',
      apiResponse: null,
      list: {},
      coins: ['bitcoin', 'litecoin', 'bitcoin-cash'],
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
      .get(`https://api.blockchair.com/${this.message}/dashboards/transaction/${this.hash}`)
      .then((response) => {
        this.apiResponse = response.data.data[Object.keys(response.data.data)]
        if (this.apiResponse) {
          this.list["fees"] = `${this.apiResponse.transaction.fee/100000000} ${this.message}`
          this.list["input amount"] = `${this.apiResponse.transaction.input_total} ${this.message}`
          this.list["output amount"] = `${this.apiResponse.transaction.output_total} ${this.message}`
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
select {
        width: 120px;
        height: 30px;
        border: 1px solid #999;
        font-size: 18px;
        color: black;
        background-color: #eee;
        border-radius: 5px;
        box-shadow: 4px 4px #ccc;
      }
</style>