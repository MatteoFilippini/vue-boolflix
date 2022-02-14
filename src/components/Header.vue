<template>
  <header>
    <input type="text" v-model="searchedMovie" placeholder="Cerca qui..." />
    <button @click="$emit('searchMovie', searchedMovie)">Cerca</button>
  </header>
</template>

<script>
export default {
  name: "Header",
  data() {
    return {
      searchedMovie: "",
    };
  },
};
</script>

<style>
</style>