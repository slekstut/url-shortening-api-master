<template>
  <div class="container">
    <div class="wrapper">
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
            mean a thing. Branded links help instil confidence in your content.
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
            where people engage with your content helps inform better decisions.
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
</template>

<script>
export default {
  name: "About",
};
</script>

<style lang="scss" scoped>
@import "../assets/scss/_variables.scss";

.container {
  background-color: $whiteSmoke;
  width: 100%;

  .wrapper {
      width: 75%;
  margin: 0 auto;

  }
}
</style>