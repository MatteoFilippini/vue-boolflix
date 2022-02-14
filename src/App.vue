<template>
  <div>
    <Header @searchMovie="searchMovie" />
    <!-- <input type="text" v-model="searchedMovie" placeholder="Cerca qui..." /> -->
    <!-- <button @click="searchMovie()">Cerca</button> -->
    <h1>FILM</h1>
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
            :src="require(`./assets/img/${movie.original_language}.png`)"
          />
        </p>
        <p v-else>
          {{ movie.original_language }}
        </p>
      </div>
      <p>{{ movie.vote_average }}</p>
      <hr />
    </div>
    <h1>SERIE</h1>
    <div v-for="serie in series" :key="serie.id">
      <h4>{{ serie.name }}</h4>
      <h5>{{ serie.original_name }}</h5>
      <div>
        <p
          v-if="
            serie.original_language === 'it' || serie.original_language === 'en'
          "
        >
          <img
            :alt="serie.original_language"
            :src="require(`./assets/img/${serie.original_language}.png`)"
          />
        </p>
        <p v-else>
          {{ serie.original_language }}
        </p>
      </div>
      <p>{{ serie.vote_average }}</p>
      <hr />
    </div>
  </div>
</template>

<script>
import axios from "axios";

import Header from "./components/Header.vue";

export default {
  name: "App",
  components: {
    Header,
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
      console.log(i);
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
