<template>
  <Autowrite text="Welcome to Your Vue.js App" :delay="100" />
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