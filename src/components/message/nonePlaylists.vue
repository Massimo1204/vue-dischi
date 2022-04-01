<template>
  <div class="warn-message">
    <h1 class="text-white text-center">
      Mi dispiace, non ci sono dischi
      <span class="text-warning">
        {{ selectedGenre }}
      </span>
      di
      <span class="text-success">
        {{ selectedArtist }}
      </span>
      .
    </h1>
  </div>
</template>

<script>
export default {
  name: "nonePlaylist",
  props: ["selectedGenre", "selectedArtist"],
};
</script>

<style></style>
