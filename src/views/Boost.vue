<template>
  <div class="boost-wrapper">
    <div class="boost-text">
      <h1>Boost your links today</h1>
        <ctaBtn class="active-btn">Get Started</ctaBtn>
    </div>
  </div>
</template>

<script>
import ctaBtn from "../components/BasicBtn.vue";

export default {
  components: { ctaBtn },
};
</script>

<style lang="scss" scoped>
@import "../assets/scss/_variables.scss";

.boost-wrapper {
  background-image: url("../assets/images/bg-boost-desktop.svg");
  background-repeat: none;
  background-position: cover;
  background-color: $darkViolet;
  margin: 0 auto;
  width: 100%;
  height: 15rem;
  display: grid;
  place-items: center;
  .boost-text {
    color: $white;
    display: grid;
    place-items: center;
  }
}

@media only screen and (max-width: 415px) {
  .boost-wrapper {
    .boost-text {
      h1 {
        font-size: 1.5rem;
      }
    }
  }
}
</style>