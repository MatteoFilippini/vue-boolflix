<template>
  <section :id="id">
    <h2 v-if="items.length">
      {{ title }}
      <span>"{{ searchedItem }}"</span>
    </h2>
    <div class="container">
      <div class="row">
        <Card
          v-for="item in items"
          :key="item.id"
          :item="item"
          @act="actMovie"
        />
      </div>
    </div>
  </section>
</template>

<script>
import Card from "./Card.vue";
export default {
  name: "Section",
  components: {
    Card,
  },
  props: ["id", "title", "items", "searchedItem"],
  methods: {
    actMovie() {
      this.$emit("act", this.act);
    },
  },
};
</script>

<style lang="scss" scoped>
h2 {
  margin: 30px 0 0 250px;
  color: white;
  span {
    font-size: 1.5rem;
  }
}
</style>