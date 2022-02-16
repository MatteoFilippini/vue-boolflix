<template>
  <div>
    <Header @search="search" />
    <Main
      :movies="movies"
      :series="series"
      :searchedItem="searchedItem"
      @act="actMovie"
    />
  </div>
</template>

<script>
// aggiungere alla card i primi 5 attori
// -chiamata api che dato il singolo movie (id) prende gli attori
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

      searchedItem: "",
      movies: [],
      cast: [],
      series: [],

      movieid: "",
    };
  },
  computed: {},
  methods: {
    // prendo l'id
    actMovie(i) {
      this.movieid = i;
    },
    search(item) {
      this.searchedItem = item;
      if (!item) {
        return;
      }

      const { key, language } = this.api;
      const config = {
        params: {
          language,
          query: item,
          api_key: key,
        },
      };

      this.fetchApi("search/movie", "movies", config);
      this.fetchApi("search/tv", "series", config);
      this.fetchApi2(this.movieid, this.api.key);
    },

    fetchApi(endpoint, target, config) {
      axios
        .get(`${this.api.uri}/${endpoint}`, config)
        .then((res) => {
          this[target] = res.data.results;
          console.log(this.attori);
        })
        .catch((err) => {
          console.log(err);
        });
    },
    fetchApi2(id, key) {
      axios
        .get(`https://api.themoviedb.org/3/movie/${id}/credits?api_key=${key}`)
        .then((res) => {
          this.cast = res.data.cast;
        })
        .catch((err) => {
          console.log(err);
        });
    },
    // api per stampare
  },
};
</script>

<style lang="scss">
@import "bootstrap";
@import "./assets/scss/style.scss";
</style>
