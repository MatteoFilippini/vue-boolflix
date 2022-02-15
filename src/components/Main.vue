<template>
  <div>
    <main>
      <h3 class="text-muted text-center">Cerca un titolo</h3>
      <h1>FILM</h1>

      <div v-for="movie in movies" :key="movie.id">
        <h4>{{ movie.title }}</h4>
        <h5>{{ movie.original_title }}</h5>
        <div>
          <p
            v-if="
              movie.original_language === 'it' ||
              movie.original_language === 'en'
            "
          >
            <img
              :alt="movie.original_language"
              :src="require(`../assets/img/${movie.original_language}.png`)"
            />
          </p>
          <p v-else>
            <img
              src="../assets/img/notImage.png"
              :alt="'{{ movie.original_language }}'"
            />
          </p>
        </div>
        <p>{{ movie.vote_average }}</p>
        <hr />
      </div>
      <h1>SERIE</h1>
      <div v-for="serie in series" :key="serie.id">
        <h4>{{ serie.name }}</h4>
        <h5>{{ serie.original_name }}</h5>
        <div>
          <p
            v-if="
              serie.original_language === 'it' ||
              serie.original_language === 'en'
            "
          >
            <img
              :alt="serie.original_language"
              :src="require(`../assets/img/${serie.original_language}.png`)"
            />
          </p>
          <p v-else>
            {{ serie.original_language }}
          </p>
        </div>
        <p>{{ serie.vote_average }}</p>
        <hr />
      </div>
    </main>
  </div>
</template>

<script>
export default {
  name: "Main",
  props: ["movies", "series"],
};
</script>

<style>
</style>