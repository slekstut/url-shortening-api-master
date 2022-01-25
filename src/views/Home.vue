<template>
  <header>
    <div class="main-text">
      <h1>More than just shorter links</h1>
      <p>
        Build your brand's recognition and get detailed insights on how your
        links are performing.
      </p>
      <GetStartedBtn class="active-btn">Get Started</GetStartedBtn>
    </div>
    <img src="../assets/images/illustration-working.svg" alt="" />
  </header>
</template>

<script>
import GetStartedBtn from "../components/BasicBtn.vue";

export default {
  name: "Home",
  components: { GetStartedBtn },
};
</script>

<style scoped lang="scss">
@import "../assets/scss/_variables.scss";

header {
  display: flex;
  width: 75%;
  margin: 0 auto;
  justify-content: space-between;
  margin-top: 5rem;
  margin-bottom: 20rem;
  position: relative;
  .main-text {
    width: 60%;
    h1 {
      font-size: 5rem;
      letter-spacing: -.2rem;
      line-height: 1.1;
      margin: 0;
      margin-bottom: .7rem;
    }
    p {
      font-size: 1.31rem;
      color: $grayishViolet;
      max-width: 85%;
      margin: 0;
      margin-bottom: 2rem;
    }
  }
  img {
    position: absolute;
    top: -5%;
    right: -28%;
    max-width: 100%;
  }
}
</style>
