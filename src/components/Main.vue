<template>
  <div>
    <section>
      <Card v-for="movie in movies" :key="movie.id" :movie="movie" />
    </section>
    <!-- <h3 class="text-muted text-center">Cerca un titolo</h3>
    <h1>FILM</h1> -->
  </div>
</template>

<script>
import Card from "./Card.vue";
export default {
  name: "Main",
  props: ["movies"],
  components: {
    Card,
  },
};
</script>

<style>
</style>