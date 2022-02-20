<template>
  <div class="container">
    <div class="wrapper">
      <div class="shortener-container">
        <div class="shortener-wrapper">
          <div class="input-link">
            <input
              type="text"
              placeholder="Shorten a link here..."
              v-model="urlValue"
              @input="clearError()"
              :class="{ 'error-inut': error }"
            />
            <ShortenBtn class="active-btn" @click="shortenUrl"
              >Shorten it!</ShortenBtn
            >
          </div>
        </div>
        <div class="error-msg" v-if="error">
          <p>Please add a link</p>
        </div>
      </div>
      <div class="url-list" v-if="urlList.length > 0">
        <div
          v-for="(url, index) in urlList"
          :key="index"
          @click="copiedClipboard = !copiedClipboard"
        >
          <div class="shortened-url">
            <div class="shortened-url__inner">
              <a href="{{ url.longUrl }}" target="_blank">{{ url.longUrl }}</a>
              <div>
                <a href="{{ url.shortUrl }}" target="_blank">{{ url.shortUrl }}</a>
                <CopyBtn
                  class="active-btn"
                  @click="url.copyClip = !url.copyClip"
                  ><span v-if="!url.copyClip">Copy</span
                  ><span v-if="url.copyClip">Copied!</span></CopyBtn
                >
              </div>
            </div>
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
import axios from "axios";
import ShortenBtn from "../components/BasicBtn.vue";
import CopyBtn from "../components/BasicBtn.vue";

export default {
  name: "About",
  components: { ShortenBtn, CopyBtn },
  data() {
    return {
      urlValue: "",
      urlList: [],
      error: false,
      copiedClipboard: false,
    };
  },
  methods: {
    shortenUrl() {
      if (!this.urlValue) {
        return (this.error = true);
      }
      const vm = this;
      axios
        .post(
          `https://api.shrtco.de/v2/shorten?url=${this.urlValue}/very/long/link.html`
        )
        .then(function (response) {
          if (response.status == 200 || response.status == 201) {
            console.log("response is: ");
            console.log(response);
            console.log(response.data.result.full_short_link2);
            const generatedShortUrl = response.data.result.full_short_link2;
            vm.urlList.push({
              longUrl: vm.urlValue,
              shortUrl: generatedShortUrl,
              copyClip: false,
            });
            vm.urlValue = "";
          } else {
            console.log("Opps dude, status code != 200 :( ");
          }
        })
        .catch(function (error) {
          console.log("Error! " + error);
        });
    },
    clearError() {
      this.error = false;
    },
  },
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
    padding-bottom: 2rem;
    .shortener-container {
      max-height: 15rem;
      max-width: 67.5rem;
      background-image: url("../assets/images/bg-shorten-desktop.svg");
      background-repeat: no-repeat;
      background-position: cover;
      background-color: $veryDarkViolet;
      margin: 0 auto;
      border-radius: 0.6rem;
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
      transform: translateY(-4.5rem);
      z-index: 0;
      .error-msg {
        margin: 0;
        padding: 0;
        color: red;
        position: absolute;
        left: 5%;
        bottom: -2%;
        transform: translate(-5%, 2%);
        text-align: left;
        font-style: italic;
      }
      .shortener-wrapper {
        padding: 3rem;
        width: 100%;
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
    .url-list {
      margin-top: -2.5rem;
      .shortened-url {
        background-color: $white;
        border-radius: 1rem;
        margin-bottom: 1rem;
        &__inner {
          display: flex;
          flex-direction: row;
          justify-content: space-between;
          align-items: center;
          padding: 1.5rem;
          a {
            color: $veryDarkBlue;
            text-decoration: none;
          }
          div {
            display: flex;
            flex-direction: row;
            gap: 2rem;
            justify-content: space-between;
            align-items: center;
            a {
              color: $cyan;
              text-decoration: none;
            }
            button {
              border-radius: 0.6rem;
            }
          }
        }
      }
    }

    .about-section {
      padding-top: 4rem;
      .text {
        margin-top: 8rem;
        display: grid;
        place-items: center;
        text-align: center;
        h1 {
          margin: 0;
        }
        p {
          width: 50%;
          color: $grayishViolet;
        }
      }
      .box-container {
        display: grid;
        grid-template-columns: repeat(3, 1fr);
        grid-column-gap: 2rem;
        grid-row-gap: 0;
        margin: 8rem 0;
        position: relative;
        .box-content {
          display: flex;
          flex-direction: column;
          max-width: 26rem;
          background-color: $white;
          padding: 3rem;
          border-radius: 0.7rem;
          position: relative;
          z-index: 2;
          &__icon {
            background-color: $darkViolet;
            width: fit-content;
            display: flex;
            justify-content: center;
            align-items: center;
            border: none;
            border-radius: 50%;
            margin: 0.2rem;
            position: absolute;
            top: -35%;
            left: 12%;
            transform: translate(-12%, 35%);
            img {
              padding: 1.8rem;
              display: block;
              width: 100%;
              height: auto;
            }
          }
          &__title {
            font-size: 1.5rem;
            font-weight: 700;
            text-transform: capitalize;
            margin: 2rem 0 1rem 0;
            text-align: left;
          }
          &__text {
            color: $gray;
            font-size: 0.9rem;
            line-height: 1.5;
          }
        }
        .box-content:nth-child(2) {
          transform: translateY(2.5rem);
        }
        .box-content:nth-child(3) {
          transform: translateY(5rem);
        }
        &:after {
          position: absolute;
          top: 58%;
          content: " ";
          z-index: 0;
          width: 60rem;
          height: 8px;
          background-color: $cyan;
        }
      }
    }
  }
}

.error-inut {
  border: red 2px solid !important;
}
</style>