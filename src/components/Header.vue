<template>
  <header>
    <div>
      <img src="../assets/img/logo-small.svg" alt="spotify logo" />
    </div>
  </header>
</template>

<script>
export default {
  name: "indexHeader",
};
</script>

<style scoped lang="scss">
@import "../style/style.scss";

header {
  background-color: $header-bg;
  div {
    padding: 1rem 1.5rem;
    img {
      height: 50px;
      width: 50px;
      border-radius: 50%;
      filter: brightness(0) saturate(100%) invert(56%) sepia(99%) saturate(385%)
        hue-rotate(89deg) brightness(99%) contrast(92%);
    }
  }
}
</style>
