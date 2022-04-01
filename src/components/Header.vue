<template>
  <header class="d-flex justify-content-between align-items-center">
    <div>
      <img src="../assets/img/logo-small.svg" alt="spotify logo" />
    </div>
    <div>
      <select
        name="Genres"
        aria-label="Default select example"
        class="form-select"
        v-model="selectedGenre"
        @change="$emit('selectGenre', selectedGenre)"
      >
        <option value="all" selected>All Genres</option>
        <option
          v-for="(element, index) in genres"
          :key="index"
          :value="element"
        >
          {{ element }}
        </option>
      </select>
    </div>
  </header>
</template>

<script>
export default {
  name: "indexHeader",
  props: ["genres"],
  data: function () {
    return {
      selectedGenre: "all",
    };
  },
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
