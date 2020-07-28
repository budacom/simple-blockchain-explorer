<template>
  <div class=transaction-record-container>
    <ul>
      <li v-for="transaction in transactions" :key="transaction.hash">
        <SendersRecipients :inputs="transaction.inputs" :outputs="transaction.outputs"/>
      </li>
    </ul>
  </div>
</template>

<script>
import SendersRecipients from './SendersRecipients.vue'

export default {
  props: {
    transactions: Array
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
li {
  list-style-type:none
}
</style>