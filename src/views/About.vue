<template>
  <div class="container">
    <div class="wrapper">
      <div class="shortener-container">
        <div class="shortener-wrapper">
          <div class="input-link">
            <input type="text" placeholder="Shorten a link here..." />
            <ShortenBtn class="active-btn">Shorten it!</ShortenBtn>
          </div>
          <div class="error-msg">
            <p>Please add a link</p>
          </div>
        </div>
      </div>
      <div class="about-section">
        <div class="text">
          <h1>Advanced Statistics</h1>
          <p>
            Track how your links are performing across the web with our advanced
            statistics dashboard.
          </p>
        </div>
        <div class="box-container">
          <div class="box-content">
            <div class="box-content__icon">
              <img
                src="../assets/images/icon-brand-recognition.svg"
                alt="Brand Recognition"
              />
            </div>
            <div class="box-content__title">Brand Recognition</div>
            <div class="box-content__text">
              Boost your brand recognition with each click. Generic links don't
              mean a thing. Branded links help instil confidence in your
              content.
            </div>
          </div>
          <div class="box-content">
            <div class="box-content__icon">
              <img
                src="../assets/images/icon-detailed-records.svg"
                alt="Detailed Records"
              />
            </div>
            <div class="box-content__title">Detailed Records</div>
            <div class="box-content__text">
              Gain insights into who is clicking your links. Knowing when and
              where people engage with your content helps inform better
              decisions.
            </div>
          </div>
          <div class="box-content">
            <div class="box-content__icon">
              <img
                src="../assets/images/icon-fully-customizable.svg"
                alt="Fully Customizable"
              />
            </div>
            <div class="box-content__title">Fully Customizable</div>
            <div class="box-content__text">
              Improve brand awareness and content discoverability through
              customizable lins, supercharging audience engagement.
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import ShortenBtn from "../components/BasicBtn.vue";

export default {
  name: "About",
  components: { ShortenBtn },
};
</script>

<style lang="scss" scoped>
@import "../assets/scss/_variables.scss";

.container {
  background-color: $whiteSmoke;
  width: 100%;
  position: relative;
  .wrapper {
    width: 75%;
    margin: 0 auto;
    .shortener-container {
      max-height: 10rem;
      max-width: 75%;
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
      position: absolute;
      top: -10%;
      left: 0;
      right: 0;
      .shortener-wrapper {
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
            border-radius: 0.6rem;
          }
        }
      }
    }
    .about-section {
      padding-top: 8rem;
      .text {
        margin-top: 8rem;
        text-align: center;
        p {
          width: 60%;
        }
      }
    }
  }
}
</style>