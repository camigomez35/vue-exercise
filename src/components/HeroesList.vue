<template>
  <div class="heroes-list">
    <hero-card
      v-for="hero in heroes"
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
import { urlAPI } from "@/credentials.js";
import getAuth from "@/utils/utils.js";

export default {
  components: {
    HeroCard
  },
  data() {
    return {
      heroes: []
    };
  },
  methods: {
    getheroes() {
      const { ts, hash, publicKey } = getAuth();
      axios
        .get(
          `${urlAPI}characters?limit=30&ts=${ts}&apikey=${publicKey}&hash=${hash}`
        )
        .then(response => {
          this.heroes = response.data.data.results;
        });
    },
  },
  mounted() {
    this.getheroes();
  }
};
</script>

<style scoped lang="scss">
.heroes-list {
  display: flex;
  flex-wrap: wrap;
  justify-content: space-around;
}
</style>
