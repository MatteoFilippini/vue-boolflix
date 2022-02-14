<template>
  <div>
    <label for="">Film</label>
    <input type="text" v-model="searchedMovie" />
    <button @click="searchMovie()">Cerca</button>
    <div v-for="movie in movies" :key="movie.id">
      <h4>{{ movie.title }}</h4>
      <h5>{{ movie.original_title }}</h5>
      <p>{{ movie.original_language }}</p>
      <p>{{ movie.vote_average }}</p>
      <hr />
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "App",
  data() {
    return {
      uri: "https://api.themoviedb.org/3/search/movie?",
      api_key: "031f0a4766b91b5ae8a907cba992f2e0",
      query: "",
      language: "it-IT",

      movies: [],
      searchedMovie: "",
    };
  },
  methods: {
    getMovies() {
      axios
        .get(
          `${this.uri}api_key=${this.api_key}&query=${this.query}&language=${this.lenguage}`
        )
        .then((res) => {
          this.movies = res.data.results;
        });
    },
    searchMovie() {
      if (!this.searchedMovie) return;
      this.query = this.searchedMovie;
      this.getMovies();
    },
  },
};
</script>

<style lang="scss">
</style>
