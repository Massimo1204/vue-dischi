<template>
  <div id="app">
    <indexHeader
      @selectGenre="copySelectedGenre"
      :genres="allGenres"
      :artists="artists"
      @selectArtist="copySelectedArtist"
    />
    <indexMain
      :selectedGenre="selectedGenre"
      @receiveGenres="copyGenres"
      @receiveArtists="copyArtists"
      :selectedArtist="selectedArtist"
    />
  </div>
</template>

<script>
import indexHeader from "./components/Header.vue";
import indexMain from "./components/Main.vue";

export default {
  name: "App",
  components: {
    indexHeader,
    indexMain,
  },
  data: function () {
    return {
      selectedGenre: "",
      selectedArtist: "",
      allGenres: null,
      artists: null,
    };
  },
  methods: {
    copySelectedGenre(selected) {
      this.selectedGenre = selected;
    },
    copySelectedArtist(artist) {
      this.selectedArtist = artist;
    },
    copyGenres(genres) {
      this.allGenres = genres;
    },
    copyArtists(artists) {
      this.artists = artists;
    },
  },
};
</script>

<style lang="scss">
@import "./style/style.scss";
@import url("https://fonts.googleapis.com/css2?family=Lato:ital,wght@0,100;0,300;0,400;0,700;0,900;1,100;1,300;1,400;1,700;1,900&display=swap");

#app {
  font-family: "Lato", sans-serif;
}
</style>
