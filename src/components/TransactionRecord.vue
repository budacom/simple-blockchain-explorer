<template>
  <div class=transaction-record-container>
    <ul>
      <li v-for="transaction in transactions" :key="transaction.hash">
        <SendersRecipients :inputs="transaction.inputs" :outputs="transaction.outputs" :denomination="denomination"/>
      </li>
    </ul>
  </div>
</template>

<script>
import SendersRecipients from './SendersRecipients.vue'

export default {
  props: {
    transactions: Array,
    denomination: String
  },
  components: {
    SendersRecipients
  },
  data () {
    console.log(this.transactions)
    return {

    }
  }
}
</script>

<style scoped>
ul {
  list-style: none;
  padding-left: 0;
}
</style>