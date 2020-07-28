<template>
  <div class=adress-info-container>
    <div class=adress-form>
      <select v-model="coin_type">
        <option value="bitcoin">Bitcoin</option>
        <option value="litecoin">Litecoin</option>
        <option value="bitcoin-cash">Bitcoin Cash</option>
      </select>
      <input v-model="adress" placeholder="Adress">
      <button @click="get_adress_info" class=search_adress_button>Search</button>
    </div>

    <div class=adress-display-container>

    </div>

    <div class=record-container>
      <button v-if="valid_adress" @click="get_transactions_info">Show last 10 transactions</button>
      <TransactionRecord v-bind:transactions="transactions_details"/>
    </div>
  </div>
</template>

<script>
import TransactionRecord from './TransactionRecord.vue'

export default {
  name: 'AdressInfo',
  props: {
    msg: String
  },
  data () {
    return {
      // Shows the history or not
      valid_adress: false,
      // Adress input
      adress: "",
      // Selected coin
      coin_type: "bitcoin",
      // Full answer given by the API
      resquest_data: null,
      // Adress info given by the API
      adress_info: [],
      // Transactions related to the adress
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
    get_adress_info: function() {
      // Clear transactionr record
      this.transactions_details = {}
      
      // Fake api call
     
      this.resquest_data = response.data.data[Object.keys(response.data.data)]
      this.adress_info = this.resquest_data.adress
      this.transactions = this.resquest_data.transactions
      this.last_transactions = this.transactions.slice(0, 10)
      this.utxo = this.resquest_data.utxo
      this.valid_adress = true

      // True API call
      // let path = 'https://api.blockchair.com/' + this.coin_type + '/dashboards/address/' + this.adress
      // this.axios
      //   .get(path)
      //   .then((response) => {
        //     if (response.status != 200) {
          //       alert("Something went wrong\nStatus " + response.status)
      //     } else {
        //       this.resquest_data = response.data.data[Object.keys(response.data.data)]
      //       this.adress_info = this.resquest_data.adress
      //       this.transactions = this.resquest_data.transactions
      //       this.last_transactions = this.transactions.slice(0, 10)
      //       this.utxo = this.resquest_data.utxo
      //       this.valid_adress = true
      //     }
      //   })
      
    },
    get_transactions_info: function() {
      
      this.transactions_details = response.data.data
    },
    isValidHttpUrl: function(string) {
      let url;

      try {
        url = new URL(string);
      } catch (_) {
        return false;  
      }

      return url.protocol === "http:" || url.protocol === "https:";
    }
  },
  components: {
    TransactionRecord
  }
}
</script>

<style scoped>
</style>