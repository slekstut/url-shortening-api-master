<template>
  <button>
    <slot></slot>
  </button>
</template>

<script>
export default {
  setup() {
    return {};
  },
};
</script>

<style lang="scss" scoped>
@import "../assets/scss/_variables.scss";

button {
  background: none;
  font-size: 1.1rem;
  padding: 1rem 2.5rem;
  color: $grayishViolet;
  font-weight: 700;
  border: none;
  border-radius: 3rem;
  text-transform: capitalize;
  transition: all 0.4s ease-in-out;
  white-space: nowrap;
  z-index: 2;
  display: flex;
  justify-content: center;
  align-items: center;
  &:hover {
    cursor: pointer;
  }
}
</style>