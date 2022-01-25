<template>
  <div>
    <Navbar />
    <Home />
    <Shortener />
    <About/>
  </div>
</template>

<script>
import Navbar from "./components/Navbar.vue";
import Home from "./views/Home.vue";
import Shortener from "./views/Shortener.vue";
import About from "./views/About.vue";

export default {
  name: "App",
  components: {
    Navbar,
    Home,
    Shortener,
    About,
  },
};
</script>

<style lang="scss">
@import "./assets/scss/_variables.scss";

html {
  box-sizing: border-box;
  scroll-behavior: smooth;
}
*,
*:before,
*:after {
  box-sizing: inherit;
}

body {
  margin: 0;
  padding: 0;
  font-family: $fontFamily;
  font-size: $fontSize;
  font-weight: $fontWeight;
  background-color: $white;
  color: $veryDarkViolet;
}

#app {
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  margin: 0 auto;
  height: 100%;
  overflow-x: hidden;
}
</style>
