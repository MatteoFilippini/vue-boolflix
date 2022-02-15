<template>
  <div>
    <h4>{{ movie.title }}</h4>
    <h5>{{ movie.original_title }}</h5>
    <div>
      <p
        v-if="
          movie.original_language === 'it' || movie.original_language === 'en'
        "
      >
        <img
          :alt="movie.original_language"
          :src="require(`../assets/img/${movie.original_language}.png`)"
        />
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
};
</script>

<style>
</style>