<template>
  <nav>
    <div class="nav-left">
      <div class="logo"><img src="../assets/images/logo.svg" alt="" /></div>
      <ul>
        <li>Features</li>
        <li>Pricing</li>
        <li>Resources</li>
      </ul>
    </div>

    <div class="auth-btns">
      <LoginBtn :class="{ 'active-btn': isActive === 1 }" @click="isActive=1">Login</LoginBtn>
      <SignupBtn :class="{ 'active-btn': isActive === 2 }" @click="isActive=2">Sign Up</SignupBtn>
    </div>
    <div class="menu-icon">
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
        margin-right: .5rem;
    }
  }
  .menu-icon {
    position: absolute;
    top: 2rem;
    right: 2rem;
    width: 32px;
    height: 26px;
    display: none;
    flex-direction: column;
    justify-content: space-between;
    .line {
      display: none;
      width: 100%;
      height: 4px;
      background: $grayishViolet;
    }
  }
}
</style>