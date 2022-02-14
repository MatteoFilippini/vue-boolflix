<template>
  <div>
    <Header @searchMovie="searchMovie" />
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
      uriMovie: "https://api.themoviedb.org/3/search/movie?",
      uriSerie: "https://api.themoviedb.org/3/search/tv?",
      api_key: "031f0a4766b91b5ae8a907cba992f2e0",
      query: "",
      language: "it-IT",

      movies: [],
      series: [],
      searchedMovie: "",
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
      if (!i) return;
      this.query = i;
      this.getMovies();
      this.getSerie();
    },
  },
};
</script>

<style lang="scss">
</style>
