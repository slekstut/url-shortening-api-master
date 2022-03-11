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

@media only screen and (max-width: 991px) {
  .footer {
    .footer-wrapper {
      gap: 1rem;
      .footer-column:first-child {
        margin-right: 1rem;
      }
      .footer-column {
        width: 100%;
        h3 {
          font-size: $fontSize;
        }
        h5 {
          font-size: $fontSize;
        }
        a {
          font-size: $font-size-md;
        }
      }
      .socials {
        a img {
          max-width: 1rem;
          height: auto;
        }
      }
    }
  }
}

@media only screen and (max-width: 768px) {
  .footer {
    .footer-wrapper {
      display: flex;
      flex-direction: row;
      justify-content: space-between;
      padding: 1.5rem 2rem;
      .footer-column {
        flex: 0 1 20%;
        align-items: center;
        h3 {
          font-size: $fontSize;
        }
        h5 {
          font-size: $fontSize;
        }
        a {
          font-size: $font-size-md;
          text-align: center;
        }
      }
      .socials {
        display: flex;
        flex-direction: column;
      }
    }
  }
}

@media only screen and (min-width: 415px) and (max-width: 580px) {
  .footer {
    .footer-wrapper {
      padding: 1rem;
      .footer-column {
        h3 {
          font-size: $font-size-md;
        }
        h5 {
          font-size: $font-size-md;
        }
        a {
          font-size: $font-size-sm;
        }
      }
    }
  }
}

@media only screen and (max-width: 415px) {
  .footer {
    .footer-wrapper {
      width: 100%;
      flex-direction: column;
      align-items: center;
      gap: 3rem;
      text-align: center;
      .footer-column:first-child {
        margin-right: 0;
      }
      .footer-column {
        width: 100%;
      }
      .socials {
        display: flex;
        flex-direction: row;
        justify-content: center;
      }
    }
  }
}
</style>