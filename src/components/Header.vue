<template>
  <header>
    <h1><a href="http://localhost:8080">BOOLFLIX</a></h1>
    <div class="searchBar">
      <i
        class="fa-solid fa-magnifying-glass me-3"
        role="button"
        @click="searchIcon = !searchIcon"
        :class="{ dnone: !searchIcon }"
      ></i>
      <input
        v-if="!searchIcon"
        type="text"
        v-model.trim="searchedItem"
        placeholder="Cerca qui..."
        @keyup.enter="search"
      />
      <!-- <button @click="search">Cerca</button> -->
    </div>
  </header>
</template>

<script>
export default {
  name: "Header",
  data() {
    return {
      searchedItem: "",
      searchIcon: true,
    };
  },
  methods: {
    search() {
      this.$emit("search", this.searchedItem);
      this.searchIcon = true;
      this.searchedItem = "";
    },
  },
};
</script>

<style lang="scss" scoped>
// .dnone {
//   display: none;
// }
header {
  height: 10vh;
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 0 50px;
  background-color: rgb(5, 5, 5);
  i {
    font-size: 1.8rem;
    color: rgba(255, 255, 255, 0.781);
  }
  h1 {
    font-weight: bold;
    a {
      text-decoration: none;
      color: rgb(234, 0, 30);
    }
  }
  .searchBar {
    display: flex;
    align-items: center;
    input {
      background-color: black;
      color: white;
      border: 1px solid white;
    }
    input:focus-visible {
      outline-width: 0;
    }
  }
}
</style>