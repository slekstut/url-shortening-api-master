<template>
  <div class="container">
    <div class="wrapper">
      <div class="input-link">
        <input type="text" placeholder="Shorten a link here..." />
        <ShortenBtn class="active-btn">Shorten it!</ShortenBtn>
      </div>
      <div class="error-msg">
        <p>Please add a link</p>
      </div>
    </div>
  </div>
</template>

<script>
import ShortenBtn from "../components/BasicBtn.vue";
export default {
  name: "Shortener",
  components: { ShortenBtn },
};
</script>

<style lang="scss" scoped>
@import "../assets/scss/_variables.scss";

.container {
  width: 75%;
  max-height: 10rem;
  background-image: url("../assets/images/bg-shorten-desktop.svg");
  background-repeat: no-repeat;
  background-position: cover;
  background-color: $veryDarkViolet;
  margin: 0 auto;
  margin-bottom: 2rem;
  border-radius: 0.6rem;
  display: flex;
  justify-content: center;
  align-items: center;
  z-index: 0;
  .wrapper {
    padding: 3rem;
    width: 100%;
    .error-msg {
      display: none;
    }
    .input-link {
      display: flex;
      flex-wrap: nowrap;
      gap: 1rem;
      width: 100%;
      input {
        width: 100%;
        padding: 0.5rem 2rem;
        border-radius: 0.6rem;
        border: none;
        font-size: 1.2rem;
        font-weight: 500;
        color: $grayishViolet;
        &::placeholder {
          font-weight: 500;
          color: $grayishViolet;
        }
        &:focus {
          outline: none;
        }
      }
      button {
          border-radius: .6rem;
      }
    }
  }
}
</style>