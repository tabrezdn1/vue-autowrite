<template>
  <Autowrite text="Welcome to Your Vue.js App" :delay="100"/>
</template>
<script>
import Autowrite from "./components/AutoWrite";
export default {
  name: "App",
  components: {
    Autowrite,
  },
};
</script>
<style>
.auto-write-2 {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #c90647;
  margin-top: 60px;
}
</style>