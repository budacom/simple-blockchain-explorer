<template>
  <div class=address-info-container>
    <div class=address-form>
      <select v-model="coin_type">
        <option value="bitcoin">Bitcoin</option>
        <option value="litecoin">Litecoin</option>
        <option value="bitcoin-cash">Bitcoin Cash</option>
      </select>
      <input v-model="address" placeholder="Address">
      <button @click="get_address_info" class=search_address_button>Search</button>
    </div>

    <div v-if="valid_address" class=results-display>
      <p>Balance: {{ this.address_info.balance }}Satoshi ({{ this.address_info.balance / 100000000}} BTC)</p>
      <button @click="get_transactions_info">Show last 10 transactions</button>
      <TransactionRecord v-bind:transactions="transactions_details"/>
    </div>
  </div>
</template>

<script>
import TransactionRecord from './TransactionRecord.vue'

export default {
  name: 'AddressInfo',
  props: {
    msg: String
  },
  data () {
    return {
      // Shows the history or not
      valid_address: false,
      // Address input
      address: "",
      // Selected coin
      coin_type: "bitcoin",
      // Full answer given by the API
      resquest_data: null,
      // Address info given by the API
      address_info: [],
      // Transactions related to the address
      transactions: [],
      // Ultimas 10 transacciones
      last_transactions: [],
      // Utxos given by the API
      utxo: [],
      // Transactions details obtained using the second API call
      transactions_details: {}
    }
  },
  methods: {
    get_address_info: function() {
      this.transactions_details = {}
      this.valid_address = false
      let path = 'https://api.blockchair.com/' + this.coin_type + '/dashboards/address/' + this.address      
      this.axios
        .get(path)
        .then((response) => {
          this.resquest_data = response.data.data[Object.keys(response.data.data)]
          this.address_info = this.resquest_data.address
          this.transactions = this.resquest_data.transactions
          this.last_transactions = this.transactions.slice(0, 10)
          this.utxo = this.resquest_data.utxo
          this.valid_address = true
        })
        .catch(error => {
          if (error.response.status == 430) {
            alert("API calls limit exceeded")
            console.log(error.response.status)
          }
        })
      
    },
    get_transactions_info: function() {
      let path = 'https://api.blockchair.com/' + this.coin_type + '/dashboards/transactions/' + this.last_transactions.join(",")
      this.axios
        .get(path)
        .then((response) => {
          this.transactions_details = response.data.data
        })
        .catch(error => {
          if (error.response.status == 430) {
            alert("API calls limit exceeded")
            console.log(error.response.status)
          }
        })
    }
  },
  components: {
    TransactionRecord
  }
}
</script>

<style scoped>
</style>