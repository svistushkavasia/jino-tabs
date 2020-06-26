<template>
  <div id="app">
    <!-- tabs -->
    <tabs :tabId="tabId" :tabs="tabs">
      <template v-slot:tab="{tab, active}">
        <!-- custom tab component for account tab -->
        <tab-account
          v-if="tab.id === 'account'"
          @click.native="tabId = tab.id"
          :tab="tab"
          :active="active"
          :currentUser="currentUser"
        ></tab-account>
        <!-- default tab component -->
        <tab v-else @click.native="tabId = tab.id" :active="active" :tab="tab"></tab>
      </template>
    </tabs>
    <!-- can be dynamic component or router-view -->
    <!-- <component :is="'page-'+tabId"></component> -->
    <!-- panels -->
    <div v-if="tabId === 'info'">
      <h1>Info</h1>
    </div>
    <div v-if="tabId === 'settings'">
      <h1>Settings</h1>
    </div>
    <div v-if="tabId === 'account'">
      <h1>Account {{currentUser.name}}</h1>
    </div>
    <div v-if="tabId === 'domains'">
      <h1>Domains</h1>
    </div>
  </div>
</template>

<script>
import tabs from "./components/tabs";
import tab from "./components/tab";
import tabAccount from "./components/tab_account";

export default {
  name: "App",
  components: {
    tabs,
    tab,
    tabAccount
  },
  data() {
    return {
      tabId: "info",
      tabs: [
        { id: "info", name: "Информация о пользователе" },
        { id: "domains", name: "Домены" },
        { id: "settings", name: "Настройки" },
        { id: "account", name: "Аккаунт" }
      ],
      currentUser: {
        name: "Oleg"
      }
    };
  },
  computed: {
    // currentUser () {
    //   return this.$store.state.auth.currentUser
    // }
  },
  methods: {
    tabClick(t) {
      console.log("tabClick", t);
      // store state in route query
      // tabId === $route.query.tab
      // this.$router.push({query: {tab: t.id}})
    }
  }
};
</script>

<style>
.br {
  border: 1px solid #FA0000;
}
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
