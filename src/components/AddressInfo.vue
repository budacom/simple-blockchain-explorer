<template>
  <div class=address-info-container>
    <div class=container>
      <div class=select-container>
        <select v-model="selected_coin" class=select-coin>
          <option value='0'>Bitcoin</option>
          <option value='1'>Litecoin</option>
        </select>
      </div>
      <div class=text-container>
        <input v-model="address" placeholder="Dirección" class=text-input>
      </div>
      <div class=button-container>
        <button @click="get_address_info" class=search-button>Buscar</button>
      </div>
    </div>

    <div v-if="valid_address" class=results-container>
      <p>Balance: {{ this.resquest_data.balance }} {{this.coins_info[this.selected_coin][3]}} ({{ this.resquest_data.balance / 100000000}} {{this.coins_info[this.selected_coin][1]}})</p>
      <p>Enviado: {{ this.resquest_data.total_sent }} {{this.coins_info[this.selected_coin][3]}} ({{ this.resquest_data.total_sent / 100000000}}  {{this.coins_info[this.selected_coin][1]}})</p>
      <p>Recibido: {{ this.resquest_data.total_received }} {{this.coins_info[this.selected_coin][3]}} ({{ this.resquest_data.total_received / 100000000}}  {{this.coins_info[this.selected_coin][1]}})</p>
      <TransactionRecord v-bind:transactions="transactions" :denomination="this.coins_info[this.selected_coin][1]"/>
    </div>
  </div>
</template>

<script>
import TransactionRecord from './TransactionRecord.vue'

export default {
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
      selected_coin: 0,
      // Coins info
      coins_info: [
        ["btc", "BTC", "Bitcoins", "Satoshi"],
        ["ltc", "LTC", "Litecoins", "Litoshi"]
      ],
      // Full answer given by the API
      resquest_data: null,
      // Transactions related to the address
      transactions: []
    }
  },
  methods: {
    get_address_info: function() {
      this.transactions_details = {}
      this.valid_address = false
      let path = 'https://api.blockcypher.com/v1/' + this.coins_info[this.selected_coin][0] + '/main/addrs/' + this.address + '/full?limit=50'
      this.axios
        .get(path)
        .then((response) => {
          this.valid_address = true
          this.resquest_data = response.data
          this.transactions = this.resquest_data.txs
        })
        .catch(error => {
        if (!error.response || error.response.status != 200) {
          alert("No fue posible acceder a la transacción dada")
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