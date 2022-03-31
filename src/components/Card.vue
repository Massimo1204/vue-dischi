<template>
  <div class="row justify-content-center gy-4 py-3">
    <div
      class="card col-2 mx-3 text-center"
      v-for="(element, index) in playlists"
      :key="index"
    >
      <div class="img-wrapper py-4 px-1">
        <img class="img-fluid" :src="element.poster" :alt="element.title" />
      </div>
      <h4 class="text-light text-uppercase">{{ element.title }}</h4>
      <div class="text-secondary fw-bold">
        <p class="mb-0 mt-3 fs-5">{{ element.author }}</p>
        <p>{{ element.year }}</p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "playlistCard",
  props: { playlists: Array },
};
</script>

<style lang="scss" scoped></style>
