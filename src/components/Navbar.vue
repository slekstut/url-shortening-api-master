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
      <button>Login</button>
      <button>Sign Up</button>
    </div>
    <div class="menu-icon">
      <span class="line"></span>
      <span class="line"></span>
      <span class="line"></span>
    </div>
  </nav>
</template>

<script>
export default {};
</script>

<style lang="scss" scoped>
@import "../assets/scss/_variables.scss";

nav {
  position: relative;
  display: flex;
  align-items: center;
  justify-content: space-between;
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
        &:hover {
          color: $veryDarkViolet;
          cursor: pointer;
        }
      }
    }
  }
  .auth-btns {
    display: flex;

    button {
      background: none;
      font-size: 1.1rem;
      padding: 1rem 2rem;
      color: $grayishViolet;
      font-weight: 700;
      border: none;
      text-transform: capitalize;
      &:hover {
        color: $white;
        background-color: $cyan;
        border-radius: 3rem;
        cursor: pointer;
      }
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