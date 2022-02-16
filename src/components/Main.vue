<template>
  <main>
    <h2 v-if="!movies.length" id="title">Cerca un film o una serie</h2>
    <section id="movies">
      <h2 v-if="movies.length">
        MOVIES <span>"{{ searchedItem }}"</span>
      </h2>
      <div class="container">
        <div class="row">
          <Card v-for="movie in movies" :key="movie.id" :item="movie" />
        </div>
      </div>
    </section>
    <section id="movies">
      <h2 v-if="movies.length">
        SERIES <span>"{{ searchedItem }}"</span>
      </h2>
      <div class="container">
        <div class="row">
          <Card v-for="serie in series" :key="serie.id" :item="serie" />
        </div>
      </div>
    </section>
  </main>
</template>

<script>
import Card from "./Card.vue";
export default {
  name: "Main",
  props: ["movies", "series", "searchedItem"],
  components: {
    Card,
  },
};
</script>

<style lang="scss" scoped>
main {
  height: 90vh;
  overflow: auto;
  #title {
    text-align: center;
    line-height: 90vh;
  }
  h2 {
    margin: 30px 0 0 250px;
    color: white;
    span {
      font-size: 1.5rem;
    }
  }
}
</style>