<template>
  <div class=senders-recipients-container>
    <table class=senders-container>
      <tr>
        <th class=left>Monto</th>
        <th class=right>Envían</th>
      </tr>
      <tr v-for="input in inputs" :key="input.spending_signature_hex">
        <td class=left> {{input.output_value / 100000000}} {{denomination}}</td>
        <td class=right> {{input.addresses[0]}} </td>
      </tr>
    </table>
    <img class=right-arrow alt="Right arrow" src="../assets/right_arrow.jpg">
    <table class=recipients-container>
      <tr>
        <th class=left>Reciben</th>
        <th class=right>Monto</th>
      </tr>
      <tr v-for="output in outputs" :key="output.spending_signature_hex">
        <td class=left> {{output.addresses[0]}} </td>
        <td class=right> {{output.value / 100000000}} {{creation_denomination}}</td>
      </tr>
    </table>
  </div>
</template>

<script>
export default {
  props: {
    inputs: Array,
    outputs: Array,
    denomination: String,
    highlighted: String
  },
  data() {
    return {
      creation_denomination: this.denomination,
      creation_highlighted: this.highlighted
    }
  }
}
</script>

<style scoped>
.left {
  text-align: left;
}
.right {
  text-align: right;
}
th {
  font-family: myriad_pro_lightregular,helvetica,arial,sans-serif;
  text-transform: uppercase;
  font-weight: lighter;
  color: #888;
  font-size: small;
}
td {
  font-family: monospace;
  font-weight: normal;
  color: rgb(43, 56, 64);
  font-size: small;
  text-align: right;
}
.senders-container {
  margin-left: 3%;
  margin-top: 10px;
  margin-bottom: 10px;
  width: 47%;
  order: 1;
  flex-grow: 1;
}
.right-arrow {
  margin-right: 3%;
  margin-left: 3%;
  width: 5%;
  order: 2;
  flex-grow: 1;

}
.recipients-container {
  margin-right: 3%;
  margin-top: 10px;
  margin-bottom: 10px;
  width: 47%;
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
  align-items: flex-start;
}
</style>