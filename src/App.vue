<template>
  <div>
    <Header @search="search" />
    <Main :movies="movies" :series="series" />
  </div>
</template>

<script>
import axios from "axios";

import Header from "./components/Header.vue";
import Main from "./components/Main.vue";

export default {
  name: "App",
  components: {
    Header,
    Main,
  },
  data() {
    return {
      api: {
        key: "031f0a4766b91b5ae8a907cba992f2e0",
        language: "it-IT",
        uri: "https://api.themoviedb.org/3",
      },

      movies: [],
      series: [],
    };
  },
  methods: {
    getMovies() {
      axios
        .get(
          `${this.uriMovie}api_key=${this.api_key}&query=${this.query}&language=${this.lenguage}`
        )
        .then((res) => {
          this.movies = res.data.results;
        });
    },
    getSerie() {
      axios
        .get(
          `${this.uriSerie}api_key=${this.api_key}&query=${this.query}&language=${this.lenguage}`
        )
        .then((res) => {
          this.series = res.data.results;
        });
    },
    searchMovie(i) {
      if (!i) {
        this.movies = [];
        return;
      }
      this.query = i;
      this.getMovies();
      this.getSerie();
    },
  },
};
</script>

<style lang="scss">
@import "bootstrap";
</style>
