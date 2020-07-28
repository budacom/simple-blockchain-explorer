<template>
  <div class=transaction-record-container>
    <ul>
      <li v-for="(transaction, hash) in transactions" :key="hash">
        <SendersRecipients :inputs="transaction.inputs" :outputs="transaction.outputs"/>
      </li>
    </ul>
  </div>
</template>

<script>
import SendersRecipients from './SendersRecipients.vue'

export default {
  name: 'TransactionRecord',
  props: {
    transactions: Array
  },
  components: {
    SendersRecipients
  }
}
</script>

<style scoped>
</style>