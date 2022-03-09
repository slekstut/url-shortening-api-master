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
              v-on:keyup.enter="shortenUrl"
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
                <a
                  href="{{url.shortUrl}}"
                  target="_blank"
                  rel="noopener noreferrer"
                  >{{ url.shortUrl }}</a
                >
                <div @click="copyURL(index)">
                  <CopyBtn class="active-btn"
                    ><span v-if="!url.copyClip">Copy</span
                    ><span v-if="url.copyClip">Copied!</span></CopyBtn
                  >
                </div>
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
      urlList: JSON.parse(localStorage.urlArray || "[]"),
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
        .post(`https://api.shrtco.de/v2/shorten?url=${this.urlValue}`)
        .then(function (response) {
          if (response.status == 200 || response.status == 201) {
            const generatedShortUrl = response.data.result.short_link;
            vm.urlList.push({
              longUrl: vm.urlValue,
              shortUrl: generatedShortUrl,
              copyClip: false,
            });
            vm.urlValue = "";
            localStorage.setItem("urlArray", JSON.stringify(vm.urlList));
            let myArray = localStorage.getItem("urlArray");
            vm.urlList = JSON.parse(myArray);
          } else {
            console.log("Opps dude, status code != 200 :( ");
          }
        })
        .catch(function (error) {
          console.log("Error! " + error);
        });
    },
    copyURL(index) {
      const selectedItem = this.urlList[index].shortUrl;
      navigator.clipboard.writeText(selectedItem);
      const myBoolean = (this.urlList[index].copyClip = true);
      console.log(myBoolean);
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
        @media (max-width: 768px) {
          position: relative;
          width: 100%;
          padding-left: 1rem;
          font-size: $font-size-md;
        }
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
          width: 100%;
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

@media only screen and (max-width: 768px) {
  .container {
    .wrapper {
      width: 95%;
      .shortener-container {
        max-width: 90%!important;
        .shortener-wrapper {
          padding: 1.2rem;
          .input-link {
            flex-direction: column;
            font-size: $font-size-md;
            input {
              padding: 1rem;
              font-size: $font-size-md;
            }
            input::placeholder {
              font-size: $font-size-md;
            }
            .active-btn {
              font-size: $font-size-md;
            }
          }
        }
      }
      .url-list {
        .shortened-url__inner {
          flex-direction: column;
          gap: 2rem;
          align-items: center;
          font-size: $font-size-md;
          div {
            width: 100%;
            display: flex;
            flex-direction: column;
            justify-content: space-between;
            font-size: $font-size-md;
            div {
              display: flex;
              justify-content: flex-end;
              button {
              font-size: $font-size-md;
              }
            }
          }
        }
      }
      .about-section {
        padding-top: 0;
        font-size: $font-size-md;
        .text {
          margin-top: 0;
          font-size: $font-size-md;
          h1 {
            font-size: $fontSize;
            margin-top: 2rem;
          }
          p {
            font-size: $font-size-md;
            width: 90%;
          }
        }
        .box-container {
          display: grid;
          grid-template-columns: 1fr;
          grid-template-rows: auto;
          justify-content: center;
          align-items: center;
          gap: 5rem;
          padding: 0 1rem;
          .box-content {
          font-size: $font-size-md;
            margin: 0 auto;
          }
          &::after {
            top: 0;
            left: 50.5%;
            transform: translateX(-50.5%);
            width: 5px;
            height: 60rem;
          }
          .box-content__icon {
            top: -35%;
            left: 50%;
            transform: translate(-50%, 35%);
          }
        }
      }
    }
  }
}

@media only screen and (min-width: 768px) {
  .container {
    .wrapper {
      .about-section {
        padding-top: 0;
        .box-container {
          .box-content {
            padding: 1rem;
            min-height: 16rem;
            .box-content__icon {
              top: -15%;
              left: 47%;
              transform: translate(-47%, -15%);
          }
          &__title {
            margin-top: 4rem;
          }
          }
          &::after {
            top: 52%;
            left: 51%;
            transform: translate(-51%, -52%);
            width: 30rem;
            height: 8px;
          }
        }
      }
    }
  }
}

@media (max-width: 392px) {
  .container {
    .wrapper {
      .about-section {
        .box-container {
          .box-content {
            .box-content__icon {
                top: -14%;
                left: 49%;
                transform: translate(-49%, -14%);
          }
          }
        }
      }
    }
  }
}
</style>