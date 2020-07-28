<template>
  <div class=senders-recipients-container>
    <table class=senders-container>
      <tr>
        <th>Ammount</th>
        <th>Senders</th>
      </tr>
      <tr v-for="input in inputs" :key="input.spending_signature_hex">
        <td> {{input.output_value}} </td>
        <td> {{input.addresses[0]}} </td>
      </tr>
    </table>
    <img class=right-arrow alt="Right arrow" src="../assets/right_arrow.jpg">
    <table class=recipients-container>
      <tr>
        <th>Recipients</th>
        <th>Ammount</th>
      </tr>
      <tr v-for="output in outputs" :key="output.spending_signature_hex">
        <td> {{output.addresses[0]}} </td>
        <td> {{output.value}} </td>
      </tr>
    </table>
  </div>
</template>

<script>
export default {
  props: {
    inputs: Array,
    outputs: Array
  }
}
</script>

<style scoped>
.senders-container {
  width: 40%;
  order: 1;
  flex-grow: 1;
}
.right-arrow {
  width: 20%;
  order: 2;
  flex-grow: 1;
}
.recipients-container {
  width: 40%;
  order: 3;
  flex-grow: 1;
}
.senders-recipients-container {
  background: rgb(241, 241, 241);
  border-width: 1px;
  border-color: lightgray;
  border-style: solid;
  border-radius: 5px;
  display: flex;
  flex-wrap: nowrap;
  justify-content: space-evenly;
  align-items: flex-start
}
</style>