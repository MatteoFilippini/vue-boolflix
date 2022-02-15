<template>
  <header>
    <input
      type="text"
      v-model.trim="searchedItem"
      placeholder="Cerca qui..."
      @keyup.enter="search"
    />
    <button @click="search">Cerca</button>
  </header>
</template>

<script>
export default {
  name: "Header",
  data() {
    return {
      searchedItem: "",
    };
  },
  methods: {
    search() {
      this.$emit("search", this.searchedItem);
    },
  },
};
</script>

<style>
</style>