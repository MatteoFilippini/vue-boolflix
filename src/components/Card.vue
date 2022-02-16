<template>
  <div class="col-3">
    <div class="card">
      <div class="card-image" @click="show = !show" :class="{ dnone: !show }">
        <img :alt="item.original_title" :src="bgImage" class="img-fluid" />
      </div>
      <div class="card-desc m-3" v-if="!show" @click="show = !show">
        <!-- TITOLO -->
        <div class="card-title text-center p-2">
          <h4>{{ item.title || item.name }}</h4>
          <h6 class="text-muted">
            {{ item.original_title || item.original_name }}
          </h6>
        </div>
        <!-- INFO -->
        <div class="card-info">
          <!-- BANDIERA -->
          <div>
            <figure v-if="hasFlag">
              <img :alt="item.original_language" :src="imageSrc" />
            </figure>
            <figure v-else>
              <img
                src="../assets/img/notImage.png"
                :alt="item.original_language"
              />
              <br />
              {{ item.original_language }}
            </figure>
          </div>
          <!-- STARS -->
          <div class="card-stars">
            <span>
              <i
                v-for="(star, i) in stars"
                :key="i"
                class="fa-solid fa-star"
                role="button"
              ></i>
            </span>
            <span>
              <i
                role="button"
                v-for="(notStar, j) in notStars"
                :key="j"
                class="fa-regular fa-star"
              ></i>
            </span>
          </div>
          <!-- TRAMA -->
          <div class="card-text">
            <p>
              {{ item.overview }}
            </p>
          </div>
        </div>
      </div>
    </div>
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
      show: true,
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
      if (this.item.poster_path) {
        return `${this.uri}${this.item.poster_path}`;
      } else {
        return require(`../assets/img/notImage.png`);
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

<style lang="scss" scoped>
.dnone {
  display: none;
}
.card {
  height: 500px;
  width: 300px;
  margin: 30px 0;
  background-color: rgb(20, 21, 24);
  border: 0;
  border-radius: 5px;
  color: white;
  .card-image {
    img {
      border-radius: 5px;
      height: 500px;
    }
  }
  .card-desc {
    height: 100%;
    overflow: auto;
    .card-title {
      min-height: 100px;
    }
    .card-stars {
      margin-bottom: 15px;
      i.fa-solid {
        color: yellow;
      }
    }
    .card-text {
      font-size: 14px;
      padding-right: 18px;
    }
  }
}
figure {
  img {
    height: 30px;
  }
}
</style>