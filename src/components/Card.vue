<template>
  <div>
    <h4>{{ item.title || item.name }}</h4>
    <h5>{{ item.original_title || item.original_name }}</h5>
    <div>
      <p v-if="hasFlag">
        <img :alt="item.original_language" :src="imageSrc" />
      </p>
      <p v-else>
        {{ item.original_language }}
      </p>
    </div>
    <p>{{ stars }}</p>
    <p><img :alt="item.original_title" :src="bgImage" /></p>
    <hr />
  </div>
</template>


<script>
export default {
  name: "Card",
  props: ["item"],
  data() {
    return {
      flags: ["it", "en"],
      uri: "https://image.tmdb.org/t/p/w342",
    };
  },
  computed: {
    imageSrc() {
      return require(`../assets/img/${this.item.original_language}.png`);
    },
    hasFlag() {
      return this.flags.includes(this.item.original_language);
    },
    bgImage() {
      return `${this.uri}${this.item.poster_path}`;
    },
    stars() {
      return Math.round(this.item.vote_average / 2);
    },
  },
};
</script>

<style>
</style>