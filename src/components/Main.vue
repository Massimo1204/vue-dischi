<template>
  <main>
    <playlistCard :playlists="ultimateFilter" />
    <nonePlaylist
      v-if="ultimateFilter == ''"
      :selectedGenre="selectedGenre"
      :selectedArtist="selectedArtist"
    />
  </main>
</template>

<script>
import axios from "axios";

import playlistCard from "./Card.vue";
import nonePlaylist from "./message/nonePlaylists.vue";

export default {
  name: "indexMain",
  props: ["selectedGenre", "selectedArtist"],
  components: {
    playlistCard,
    nonePlaylist,
  },
  data: function () {
    return {
      playlistsApiUrl:
        " https://flynn.boolean.careers/exercises/api/array/music",
      playlists: null,
      genres: [],
      artists: [],
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
            if (!this.artists.includes(element.author)) {
              this.artists.push(element.author);
            }
          });
        })
        .catch((error) => {
          console.error(error);
        });
    },
    filterLayer(toFilter, arrayToFilter, attribute) {
      let displayedPlaylists;
      if (toFilter != "all" && this.playlists) {
        displayedPlaylists = arrayToFilter.filter((element) =>
          element[attribute].includes(toFilter)
        );
      } else {
        displayedPlaylists = arrayToFilter;
      }
      return displayedPlaylists;
    },
  },
  computed: {
    ultimateFilter() {
      let toDisplay;
      if (this.selectedGenre != "all" && this.selectedArtist != "all") {
        toDisplay = this.filterLayer(
          this.selectedGenre,
          this.playlists,
          "genre"
        );
        toDisplay = this.filterLayer(this.selectedArtist, toDisplay, "author");
      } else if (this.selectedGenre == "all" && this.selectedArtist != "all") {
        toDisplay = this.filterLayer(
          this.selectedArtist,
          this.playlists,
          "author"
        );
      } else if (this.selectedGenre != "all" && this.selectedArtist == "all") {
        toDisplay = this.filterLayer(
          this.selectedGenre,
          this.playlists,
          "genre"
        );
      } else {
        toDisplay = this.playlists;
      }
      return toDisplay;
    },
  },
  created: function () {
    this.getApiItems(this.playlistsApiUrl);
    this.$emit("receiveGenres", this.genres);
    this.$emit("receiveArtists", this.artists);
  },
};
</script>

<style lang="scss" scoped>
@import "../style/style.scss";

main {
  background-color: $main-bg;
  min-height: calc(100vh - (50px + 3rem));
}
</style>
