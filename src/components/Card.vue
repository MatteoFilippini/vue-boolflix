<template>
  <div>
    <h4>{{ movie.title }}</h4>
    <h5>{{ movie.original_title }}</h5>
    <div>
      <p v-if="hasFlag">
        <img :alt="movie.original_language" :src="imageSrc" />
      </p>
      <p v-else>
        {{ movie.original_language }}
      </p>
    </div>
    <p>{{ movie.vote_average }}</p>
    <hr />
  </div>
</template>

<script>
export default {
  name: "Card",
  props: ["movie"],
  data() {
    return {
      flags: ["it", "en"],
    };
  },
  computed: {
    imageSrc() {
      return require(`../assets/img/${this.movie.original_language}.png`);
    },
    hasFlag() {
      return this.flags.includes(this.movie.original_language);
    },
  },
};
</script>

<style>
</style>