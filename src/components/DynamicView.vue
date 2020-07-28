<template>
      <div id="dynamic-component-demo" class="demo">
        <button
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
          name: "Transaction",
          component: TxFinder
        },
        {
          name: "Address",
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

      .tab-button {
        padding: 6px 10px;
        border-top-left-radius: 3px;
        border-top-right-radius: 3px;
        border: 1px solid #ccc;
        cursor: pointer;
        background: #f0f0f0;
        margin-bottom: -1px;
        margin-right: -1px;
      }

      .tab-button:hover {
        background: #e0e0e0;
      }

      .tab-button.active {
        background: #e0e0e0;
      }

      .tab {
        border: 1px solid #ccc;
        padding: 10px;
      }
</style>