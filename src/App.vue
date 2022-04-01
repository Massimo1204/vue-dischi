<template>
  <div id="app">
    <indexHeader @selectGenre="sendSelectedGenre" :genres="allGenres" />
    <indexMain :selectedGenre="selectedGenre" @receiveGenres="copyGenres" />
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
      selectedGenre: "all",
      allGenres: null,
    };
  },
  methods: {
    sendSelectedGenre(selected) {
      this.selectedGenre = selected;
    },
    copyGenres(genres) {
      this.allGenres = genres;
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
