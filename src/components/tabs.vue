<template>
  <div class="container">
    <div class="tabs">
      <div class="grid-tab" v-for="tab in tabs" :key="tab.id">
        <slot name="tab" :tab="tab" :active="tabId === tab.id"></slot>
        <!-- tab active indicator -->
        <div v-if="tabId === tab.id" class="tab-active-indicator"></div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "tabs",
  props: {
    tabId: { type: String },
    tabs: {
      type: Array,
      default() {
        return [];
      }
    }
  },
  data() {
    return {};
  },
  methods: {}
};
</script>

<style>
.grid-tab {
  position: relative;
  grid-row: 1;
}
.tab-active-indicator {
  position: absolute;
  z-index: 100;
  bottom: -1px;
  width: 100%;
  height: 1px;
  background: white;
}
.tabs {
  width: 100%;
  justify-content: start;
  align-content: center;
  position: relative;
  grid-template-rows: [line1] auto;
  display: grid;
  border-bottom: 1px solid #cccccc;
  padding: 0 20px;
}
</style>
