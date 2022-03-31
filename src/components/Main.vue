<template>
  <main>
    <div class="container p-5">
      <playlistCard :playlists="playlists" />
    </div>
  </main>
</template>

<script>
import axios from "axios";

import playlistCard from "./Card.vue";

export default {
  name: "indexMain",
  components: {
    playlistCard,
  },
  data: function () {
    return {
      playlistsApiUrl:
        " https://flynn.boolean.careers/exercises/api/array/music",
      playlists: null,
    };
  },
  methods: {
    getApiItems(apiUrl) {
      axios
        .get(apiUrl)
        .then((item) => {
          this.playlists = item.data.response;
        })
        .catch((error) => {
          console.error(error);
        });
    },
  },
  created: function () {
    this.getApiItems(this.playlistsApiUrl);
  },
};
</script>

<style lang="scss" scoped>
@import "../style/style.scss";

main {
  background-color: $main-bg;
}
</style>
