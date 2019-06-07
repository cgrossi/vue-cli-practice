<template>
  <div id="app">
    <app-header></app-header>
    <Main></Main>
    <Copyright></Copyright>
  </div>
</template>

<script>
import MyHeader from "./components/MyHeader.vue";
import Copyright from "./components/MyFooter.vue";
import Main from "./components/MyMain.vue";
export default {
  name: "app",
  components: {
    "app-header": MyHeader,
    Copyright,
    Main
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin: 0;
}

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

h2 {
  padding: 8px 0;
}
</style>
