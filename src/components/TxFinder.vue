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
    <p> Searching for transaction: {{ this.hash }} in {{ this.message }}</p>
    <button
            type="button"
            class="btn"
            @click="getTx"
          >
            Search
          </button>
    <p v-if="apiResponse"> {{ this.apiResponse }}</p>
    <div v-for="(value, name) in list" :key="name">
      {{ name }}: {{ value }}
    </div>
  </div>
</template>

<script>

export default {
    data() {
    return {
      message:'bitcoin',
      hash:'',
      apiResponse: null,
      list: {},
      coins: ['bitcoin', 'litecoin', 'bitcoin-cash'],
    };
  },
  methods: {
    getTx() {
      this.axios
      .get(`https://api.blockchair.com/${this.message}/dashboards/transaction/${this.hash}`)
      .then((response) => {
        this.apiResponse = response.data.data[Object.keys(response.data.data)]
        if (this.apiResponse) {
          this.list["fees"] = `${this.apiResponse.transaction.fee} SAT`
          this.list["input amount"] = `${this.apiResponse.transaction.input_total} BTC`
          this.list["output amount"] = `${this.apiResponse.transaction.output_total} BTC`
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