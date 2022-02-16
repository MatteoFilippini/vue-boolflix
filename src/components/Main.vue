<template>
  <main>
    <h2 v-if="!movies.length">Cerca un film o una serie tv</h2>
    <Section
      id="movies"
      title="Film"
      :items="movies"
      :searchedItem="searchedItem"
      @act="actMovie"
    />
    <Section
      id="series"
      title="Serie TV"
      :items="series"
      :searchedItem="searchedItem"
      @act="actMovie"
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
  methods: {
    actMovie() {
      this.$emit("act", this.act);
    },
  },
};
</script>

<style lang="scss" scoped>
main {
  height: 90vh;
  overflow: auto;
  background-color: black;
  h2 {
    text-align: center;
    line-height: 90vh;
    color: rgb(199, 199, 199);
  }
}
</style>