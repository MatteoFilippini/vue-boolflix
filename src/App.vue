<template>
  <div>
    <label for="">Film</label>
    <input type="text" v-model="searchedMovie" />
    <button @click="searchMovie()">Cerca</button>
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

      movies: [],
      searchedMovie: "",
    };
  },
  methods: {
    getMovies() {
      axios
        .get(`${this.uri}api_key=${this.api_key}&query=${this.query}`)
        .then((res) => {
          this.movies = res.data.results;
          console.log(this.movies);
        });
    },
    searchMovie() {
      this.query = this.searchedMovie;
      this.getMovies();
    },
  },
};
</script>

<style lang="scss">
</style>
