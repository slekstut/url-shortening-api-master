<template>
  <nav>
    <div class="nav-left">
      <div class="logo"><img src="../assets/images/logo.svg" alt="" /></div>
      <div>
        <ul :class="{ 'active-mobile-menu': activeMobileMenu }">
          <li>Features</li>
          <li>Pricing</li>
          <li>Resources</li>
          <li class="user-action">
            <LoginBtn
              :class="{ 'active-btn': isActive === 1 }"
              @click="isActive = 1"
              >Login</LoginBtn
            >
          </li>
          <li class="user-action">
            <SignupBtn
              :class="{ 'active-btn': isActive === 2 }"
              @click="isActive = 2"
              >Sign Up</SignupBtn
            >
          </li>
        </ul>
      </div>
    </div>
    <div class="menu-icon" @click="activeMobileMenu = !activeMobileMenu">
      <span class="line"></span>
      <span class="line"></span>
      <span class="line"></span>
    </div>
  </nav>
</template>

<script>
import LoginBtn from "../components/BasicBtn.vue";
import SignupBtn from "../components/BasicBtn.vue";
export default {
  components: { LoginBtn, SignupBtn },
  data() {
    return {
      isActive: 2,
      activeMobileMenu: false,
    };
  },
};
</script>

<style lang="scss" scoped>
@import "../assets/scss/_variables.scss";

nav {
  position: relative;
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 1rem 0;
  width: 75%;
  margin: 0 auto;
  .nav-left {
    display: flex;
    .logo {
      display: flex;
      align-items: center;
      justify-content: center;
    }
    ul {
      display: flex;
      list-style: none;
      li {
        font-size: 1.1rem;
        margin-right: 2rem;
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
    }
  }
  .auth-btns {
    display: flex;
    button:first-child {
      margin-right: 0.5rem;
    }
  }
  .menu-icon {
    display: none;
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
        flex-direction: column;
        justify-content: center;
        align-items: center;
        padding-top: 2.5rem;
        padding-bottom: 1rem;
        background-color: $darkViolet;
        position: absolute;
        top: 4rem;
        left: 50%;
        transform: translate(-50%);
        width: 100%;
        min-height: 25rem;
        height: 100%;
        z-index: 100;
        border-radius: 0.7rem;
        li {
          color: $white;
          margin-bottom: 2rem;
        }
        li.user-action {
          width: 90%;
          display: flex;
          justify-content: center;
        }
        li:nth-child(4) {
          border-top: 1px solid $gray;
          width: 90%;
          button {
            margin-top: 2rem;
            margin-right: auto;
            margin-left: auto;
          }
        }
        .user-action {
          button {
            color: $white;
            margin-bottom: 2rem;
            margin: 0;
          }
          .active-btn {
            width: 100%;
          }
        }
      }
    }
    .auth-btns {
      display: flex;
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