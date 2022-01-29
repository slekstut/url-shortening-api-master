<template>
  <div>
    <Navbar />
    <Home />
    <About/>
    <Boost/>
  </div>
</template>

<script>
import Navbar from "./components/Navbar.vue";
import Home from "./views/Home.vue";
import About from "./views/About.vue";
import Boost from "./views/Boost.vue";

export default {
  name: "App",
  components: {
    Navbar,
    Home,
    About,
    Boost
  },
};
</script>

<style lang="scss">
@import "./assets/scss/_variables.scss";

html {
  box-sizing: border-box;
  scroll-behavior: smooth;
  max-width: 1440px;
  margin: 0 auto;

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
  height: 100%;
  overflow-x: hidden;
}
</style>
