<style>
.account-logo {
  width: 30px;
  height: 30px;
  border-radius: 50%;
  background: #eee;
  cursor: pointer;
}
</style>

<template>
  <div :class="{'tab': true, 'active': active}">
    <!-- <div class="account-logo"></div> -->
    <span>{{currentUser.name}}</span>
  </div>
</template>

<script>
export default {
  name: "tabAccount",
  props: ["tab", "active", "currentUser"],
  data() {
    return {};
  }
};
</script>
