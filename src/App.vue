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
      series: [],
    };
  },
  computed: {},
  methods: {
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
    },

    fetchApi(endpoint, target, config) {
      axios
        .get(`${this.api.uri}/${endpoint}`, config)
        .then((res) => {
          this[target] = res.data.results;
        })
        .catch((err) => {
          console.log(err);
        });
    },
  },
};
</script>

<style lang="scss">
@import "bootstrap";
@import "./assets/scss/style.scss";
</style>
