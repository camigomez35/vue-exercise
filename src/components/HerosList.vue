<template>
  <div class="heros-list">
    <hero-card
      v-for="hero in heros"
      :key="hero.id"
      :name="hero.name"
      :description="hero.description"
      :thumbnail="`${hero.thumbnail.path}.${hero.thumbnail.extension}`"
    ></hero-card>
  </div>
</template>

<script>
import axios from "axios";
import HeroCard from "@/components/HeroCard.vue";
import credentials from "@/credentials.js";
import md5 from "js-md5";

export default {
  components: {
    HeroCard
  },
  data() {
    return {
      heros: []
    };
  },
  methods: {
    getAuth() {
      const ts = Date.now();
      const hash = md5(
        ts + credentials.MARVEL_KEY_PRIVATE + credentials.MARVEL_KEY_PUBLIC
      );
      return { ts, hash };
    },
    getHeros() {
      const { ts, hash } = this.getAuth();
      axios
        .get(
          `${credentials.urlAPI}characters?limit=30&ts=${ts}&apikey=${credentials.MARVEL_KEY_PUBLIC}&hash=${hash}`
        )
        .then(response => {
          this.heros = response.data.data.results;
        });
    },
  },
  mounted() {
    this.getHeros();
  }
};
</script>

<style scoped lang="scss">
.heros-list {
  display: flex;
  flex-wrap: wrap;
  justify-content: space-around;
}
</style>
