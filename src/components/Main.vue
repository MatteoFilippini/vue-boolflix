<template>
  <div>
    <section>
      MOVIE
      <Card v-for="movie in movies" :key="movie.id" :item="movie" />
    </section>
    <section>
      SERIE
      <Card v-for="serie in series" :key="serie.id" :item="serie" />
    </section>
  </div>
</template>

<script>
import Card from "./Card.vue";
export default {
  name: "Main",
  props: ["movies", "series"],
  components: {
    Card,
  },
};
</script>

<style>
</style>