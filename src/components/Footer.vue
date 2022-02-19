<template>
  <footer class="footer">
    <div class="footer-wrapper">
      <div class="footer-column">
        <h3>Shortly</h3>
      </div>
      <div class="footer-column">
        <h5>Features</h5>
        <a href="#">Link Shortening</a>
        <a href="#">Branded Links</a>
        <a href="#">Analytics</a>
      </div>
      <div class="footer-column">
        <h5>Resources</h5>
        <a href="#">Blog</a>
        <a href="#">Developers</a>
        <a href="#">Support</a>
      </div>
      <div class="footer-column">
        <h5>Company</h5>
        <a href="#">About</a>
        <a href="#">Our Team</a>
        <a href="#">Careers</a>
        <a href="#">Contacts</a>
      </div>
      <div class="footer-column socials">
        <a href="#"
          ><img src="../assets/images/icon-facebook.svg" alt="facebok"
        /></a>
        <a href="#"
          ><img src="../assets/images/icon-twitter.svg" alt="twitter"
        /></a>
        <a href="#"
          ><img src="../assets/images/icon-pinterest.svg" alt="pinterest"
        /></a>
        <a href="#"
          ><img src="../assets/images/icon-instagram.svg" alt="instagram"
        /></a>
      </div>
    </div>
  </footer>
</template>

<script>
export default {};
</script>

<style lang="scss" scoped>
@import "../assets/scss/_variables.scss";

.footer {
  .footer-wrapper {
    display: flex;
    flex-direction: row;
    justify-content: space-between;
    background-color: $veryDarkViolet;
    color: $white;
    padding: 3rem 4rem;
    .footer-column {
      display: flex;
      flex-direction: column;
      justify-content: flex-start;
      gap: 1rem;
      h3 {
        margin: 0;
        font-size: 2rem;
      }
      h5 {
        font-size: 1.1rem;
        margin: 0;
        margin-bottom: 1.2rem;
      }
      a {
        font-size: 1.1rem;
        font-weight: 500;
        text-decoration: none;
        color: $grayishViolet;
      }
      &:nth-child(1) {
        justify-content: flex-start;
        width: 25%;
      }
      &:last-child {
          width: 25%;
      }
    }
    .socials {
      display: flex;
      flex-direction: row;
      gap: 2rem;
      justify-content: flex-end;
    }
  }
}
</style>