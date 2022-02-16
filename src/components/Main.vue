<template>
  <main>
    <h2 v-if="!movies.length" id="title">Cerca un film o una serie</h2>
    <Section
      id="movies"
      title="Film"
      :items="movies"
      :searchedItem="searchedItem"
    />
    <Section
      id="series"
      title="Serie TV"
      :items="series"
      :searchedItem="searchedItem"
    />
  </main>
</template>

<script>
import Section from "./Section.vue";
export default {
  name: "Main",
  props: ["movies", "series", "searchedItem"],
  components: {
    Section,
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
}
</style>