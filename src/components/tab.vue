<style>
.tab {
  cursor: pointer;
  padding: 15px;
  grid-row: 1;
  border-radius: 10px 10px 0px 0px;
  font-size: 16px;
}
.active {
  border: 1px solid #cccccc;
  border-bottom: none;
}
.tab-name {
  user-select: none;
  cursor: pointer;
}
.tab-over:hover {
  border-bottom: none;
  text-decoration: underline;
}
</style>

<template>
  <div :class="{'tab': true, 'active': active, 'tab-over': !active}">
    <span class="tab-name">{{tab.name}}</span>
  </div>
</template>

<script>
export default {
  name: "tab",
  props: {
    tab: { type: String },
    active: { type: Boolean }
  },
  data() {
    return {
      isOver: false
    };
  }
};
</script>

