<template>
  <nav>
    <div class="nav-left">
      <div class="logo"><img src="../assets/images/logo.svg" alt="logo" /></div>
      <ul :class="{ 'active-mobile-menu': activeMobileMenu }">
        <li>Features</li>
        <li>Pricing</li>
        <li>Resources</li>
        <li id="login">
          <LoginBtn
            :class="{ 'active-btn': isActive === 1 }"
            @click="isActive = 1"
          >
            Login
          </LoginBtn>
        </li>
        <li id="signup">
          <SignupBtn
            :class="{ 'active-btn': isActive === 2 }"
            @click="isActive = 2"
          >
            Sign Up
          </SignupBtn>
        </li>
      </ul>
    </div>
    <div class="menu-icon" @click="activeMobileMenu = !activeMobileMenu">
      <span class="line"></span>
      <span class="line"></span>
      <span class="line"></span>
    </div>
  </nav>
</template>

<script>
import LoginBtn from '../components/BasicBtn.vue'
import SignupBtn from '../components/BasicBtn.vue'
export default {
  components: {
    LoginBtn,
    SignupBtn,
  },
  data() {
    return {
      isActive: 2,
      activeMobileMenu: false,
    }
  },
}
</script>

<style lang="scss" scoped>
@import '../assets/scss/_variables.scss';

nav {
  position: relative;
  display: flex;
  align-items: center;
  padding: 1rem 0;
  width: 75%;
  margin: 0 auto;

  .nav-left {
    width: 100%;
    display: flex;
    justify-content: flex-start;
    align-items: center;

    .logo {
      width: 15%;
      display: flex;
      align-items: center;
      justify-content: flex-start;
    }

    ul {
      width: 100%;
      display: grid;
      grid-template-columns: repeat(8, 1fr);
      align-items: center;
      list-style: none;
      li {
        margin-right: 1.5rem;
        font-size: 1.1rem;
        color: $grayishViolet;
        font-weight: 700;
        text-transform: capitalize;
        transition: all 0.4s ease-in-out;

        &:hover {
          color: $veryDarkViolet;
          cursor: pointer;
          transition: transform 0.4s ease-in-out;
        }
      }
      #login {
        grid-column: 7 / 8;
        margin-right: 0;
      }
      #signup {
        grid-column: 8 / 9;
        margin-right: 0;
      }
    }
  }

  .menu-icon {
    display: none;
  }
}

@media only screen and (max-width: 991px) {
  nav {
    .nav-left {
      ul {
        li {
          font-size: $font-size-md;
        }
        #login {
        button {
        font-size: $font-size-md;
        }
      }
      #signup {
       button {
        font-size: $font-size-md;
        }
      }
      }
    }
  }
}

@media only screen and (max-width: 768px) {
  nav {
    width: 90%;
    .nav-left {
      ul {
        display: none;
      }
      .active-mobile-menu {
        display: flex;
        gap: 2rem;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        padding: 3rem 1rem;
        background-color: $darkViolet;
        position: absolute;
        top: 4rem;
        left: 50%;
        transform: translate(-50%);
        max-width: 95%;
        min-height: 27rem;
        height: 100%;
        z-index: 100;
        border-radius: 0.7rem;
        li {
          color: $white;
          font-size: $fontSize;
          margin-right: 0;
        }

        #signup, #login {
          width: 90%;
          display: flex;
          justify-content: center;
           button {
            color: $white;
            margin-bottom: 2rem;
            margin: 0;
          }
          .active-btn {
            width: 100%;
          }
        }

        #login {
          border-top: 1px solid $gray;
          width: 90%;
          button {
            font-size: $fontSize;
            margin-top: 2rem;
            margin-right: auto;
            margin-left: auto;
          }
        }
        #signup {
          button {
            font-size: $fontSize;
          }
        }
      }
    }

    .menu-icon {
      display: flex;
      position: absolute;
      top: 1rem;
      right: 0.5rem;
      width: 32px;
      height: 26px;
      flex-direction: column;
      justify-content: space-between;

      .line {
        display: block;
        width: 100%;
        height: 3px;
        border-radius: 5px;
        background: $grayishViolet;
      }
    }
  }
}
</style>
