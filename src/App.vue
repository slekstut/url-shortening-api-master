<template>
<div>
<Navbar />
  <Home />
</div>
</template>

<script>
import Navbar from "./components/Navbar.vue";
import Home from "./views/Home.vue";

export default {
  name: "App",
  components: {
    Navbar,
    Home,
  },
};
</script>

<style lang="scss">
@import "./assets/scss/_variables.scss";

#app {
  font-family: $fontFamily;
  font-size: $fontSize;
  font-weight: $fontWeight;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  max-width: 1440px;
  margin: 0 auto;
}
</style>
