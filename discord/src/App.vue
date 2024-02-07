<template>
  <div id="app">
    <Message />
  </div>
</template>

<script>
import Message from "./components/Message";

export default {
  name: "App",
  components: {
    Message,
  },
};
</script>

<style>
html,
body {
  height: 100%;
}
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  padding: 10%;
  height: inherit;
  position: relative;
  top: 40%;
}
</style>
