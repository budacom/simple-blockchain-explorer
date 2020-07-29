<template>
      <div id="dynamic-component-demo" class="demo">
        <button
          class="tabs"
          v-for="tab in tabs"
          v-bind:key="tab.name"
          v-bind:class="['tab-button', { active: currentTab.name === tab.name }]"
          v-on:click="currentTab = tab"
        >
          {{ tab.name }}
        </button>

        <component v-bind:is="currentTab.component" class="tab"></component>

    </div>
</template>

<script>

import TxFinder from './TxFinder.vue'
import AddressInfo from './AddressInfo.vue'

export default {
  data () {
  return {
    currentTab:'',
    tabs: [
        {
          name: "Transacción",
          component: TxFinder
        },
        {
          name: "Dirección",
          component: AddressInfo
        },
      ],
  };
  },
  components: {
    TxFinder,
    AddressInfo
  }
}
</script>

<style scoped>
  .tabs {
    height: 40px;
    width: 200px;
    font-size: 30px;
    font-family: sans-serif;
  color:#fff;
  margin-right: 1px;
  background-color:#1976d2;
  font-size:1.1em;
  border:0;
  cursor:pointer;
  margin-bottom: 20px;
  margin-top: 30px;
  }

  .tabs:focus {
  background-color: darkblue;
  }
</style>