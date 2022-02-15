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
    <!-- STARS -->
    <div>
      {{ stars }}
      <p>
        <i v-for="(star, i) in stars" :key="i" class="fa-solid fa-star"></i>
      </p>
      <p>
        <i
          v-for="(notStar, j) in notStars"
          :key="j"
          class="fa-solid fa-star fa-2x"
        ></i>
      </p>
    </div>

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
      if (this.item.poster_path === null) {
        return require(`../assets/img/notImage.png`);
      } else {
        return `${this.uri}${this.item.poster_path}`;
      }
    },
    stars() {
      return Math.round(this.item.vote_average / 2);
    },
    notStars() {
      return 5 - this.stars;
    },
  },
};
</script>

<style>
</style>