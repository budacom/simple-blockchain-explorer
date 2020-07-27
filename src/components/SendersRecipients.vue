<template>
  <div class=senders-recipients-container>
    <table class=senders-container>
      <tr>
        <th>Ammount</th>
        <th>Senders</th>
      </tr>
      <tr v-for="sender in senders" :key="sender">
        <td> {{sender.value}} </td>
        <td> {{sender.recipient}} </td>
      </tr>
    </table>
    <table class=recipients-container>
      <tr>
        <th>Recipients</th>
        <th>Ammount</th>
      </tr>
      <tr v-for="recipient in recipients" :key="recipient">
        <td> {{recipient.recipient}} </td>
        <td> {{recipient.value}} </td>
      </tr>
    </table>
  </div>    
</template>

<script>
export default {
  name: 'SendersRecipients',
  props: {
    inputs: Array,
    outputs: Array
  },
  data () {
    console.log(this.inputs)
    console.log(this.outputs)
    return {
      senders: this.inputs,
      recipients: this.outputs
    }
  }
}
</script>

<style scoped>
.senders-container {
  margin-left: 10%;
  margin-right: 10%;
  order: 1;
  flex-grow: 1;
}
.recipients-container {
  margin-left: 10%;
  margin-right: 10%;
  order: 2;
  flex-grow: 1;
}
.senders-recipients-container {
  background: lightgray;
  display: flex;
  flex-wrap: nowrap;
  justify-content: space-evenly;
  align-items: flex-start
}
</style>