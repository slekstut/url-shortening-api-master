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
    <img
      src="../assets/images/illustration-working.svg"
      alt="illustration-working"
    />
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
      letter-spacing: -0.2rem;
      line-height: 1.1;
      margin: 0;
      margin-bottom: 0.7rem;
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

@media only screen and (max-width: 768px) {
  header {
    width: 95%;
    margin-top: 0;
    flex-direction: column;
    .main-text {
      widows: 100%;
      order: 2;
      h1 {
        width: 100%;
        font-size: 2rem;
        font-weight: 700;
        text-align: center;
        letter-spacing: 0;
        line-height: 1.5;
      }
    }
    img {
      order: 1;
      position: relative;
      min-width: 28rem;
      top: 0;
      right: -5%;
      transform: translate(5%, 0%);
    }
  }
}
</style>
