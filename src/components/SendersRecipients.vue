<template>
  <div class=senders-recipients-container>
    <table class=senders-container>
      <tr>
        <th>Ammount</th>
        <th>Senders</th>
      </tr>
      <tr v-for="input in inputs" :key="input.spending_signature_hex">
        <td> {{input.value}} </td>
        <td> {{input.recipient}} </td>
      </tr>
    </table>
    <table class=recipients-container>
      <tr>
        <th>Recipients</th>
        <th>Ammount</th>
      </tr>
      <tr v-for="output in outputs" :key="output.spending_signature_hex">
        <td> {{output.recipient}} </td>
        <td> {{output.value}} </td>
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