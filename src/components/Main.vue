<template>
  <main>
    <playlistCard :playlists="filterPlaylists" />
  </main>
</template>

<script>
import axios from "axios";

import playlistCard from "./Card.vue";

export default {
  name: "indexMain",
  props: ["selectedGenre"],
  components: {
    playlistCard,
  },
  data: function () {
    return {
      playlistsApiUrl:
        " https://flynn.boolean.careers/exercises/api/array/music",
      playlists: null,
      genres: [],
    };
  },
  methods: {
    getApiItems(apiUrl) {
      axios
        .get(apiUrl)
        .then((item) => {
          this.playlists = item.data.response;
          this.playlists.forEach((element) => {
            if (!this.genres.includes(element.genre)) {
              this.genres.push(element.genre);
            }
          });
        })
        .catch((error) => {
          console.error(error);
        });
    },
  },
  computed: {
    filterPlaylists() {
      let displayedPlaylists;
      if (this.selectedGenre != "all" && this.playlists) {
        displayedPlaylists = this.playlists.filter((element) =>
          element.genre.includes(this.selectedGenre)
        );
      } else {
        displayedPlaylists = this.playlists;
      }
      return displayedPlaylists;
    },
  },
  created: function () {
    this.getApiItems(this.playlistsApiUrl);
    this.$emit("receiveGenres", this.genres);
  },
};
</script>

<style lang="scss" scoped>
@import "../style/style.scss";

main {
  background-color: $main-bg;
}
</style>
