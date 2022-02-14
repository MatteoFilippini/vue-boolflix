<template>
  <div>
    <label for="">Film</label>
    <input type="text" v-model="searchedMovie" />
    <button @click="searchMovie()">Cerca</button>
    <div v-for="movie in movies" :key="movie.id">
      <h4>{{ movie.title }}</h4>
      <h5>{{ movie.original_title }}</h5>
      <div>
        <p
          v-if="
            movie.original_language === 'it' || movie.original_language === 'en'
          "
        >
          <img
            :alt="movie.original_language"
            :src="`./assets/img/${movie.original_language}.png`"
          />
        </p>
        <p v-else>
          {{ movie.original_language }}
        </p>
      </div>

      <!-- <p
        v-if="
          (movie.original_language !== 'en') &
          (movie.original_language !== 'it')
        "
      >
        {{ movie.language }}
      </p>
      <p v-else-if="movie.original_language === 'it'">
        <img src="./assets/img/it.png" alt="" />
      </p>
      <p v-else-if="movie.original_language === 'en'">
        <img src="./assets/img/en.png" alt="" />
      </p> -->
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
