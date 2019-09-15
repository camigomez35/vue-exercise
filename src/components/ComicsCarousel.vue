<template>
  <div class="comics-carousel">
    <div
      class="comics-carousel__arrow comics-carousel__arrow--left"
      @click="moveCarousel(-1)"
      :disabled="atHeadOfList"
    ></div>
    <div class="comics-carousel__container">
      <div class="comics-carousel__cards" :style="{ transform: `translateX(${currentOffset}px)`}">
        <comic-card
          v-for="comic in comics"
          :key="comic.id"
          :name="comic.title"
          :description="comic.description"
          :thumbnail="`${comic.thumbnail.path}.${comic.thumbnail.extension}`"
          class="comics-carousel__slide"
        ></comic-card>
      </div>
    </div>
    <div
      class="comics-carousel__arrow comics-carousel__arrow--right"
      @click="moveCarousel(1)"
      :disabled="atEndOfList"
    ></div>
  </div>
</template>

<script>
import axios from "axios";
import ComicCard from "@/components/ComicCard.vue";
import { urlAPI } from "@/credentials.js";
import getAuth from "@/utils/utils.js";

export default {
  components: {
    ComicCard
  },
  data() {
    return {
      currentOffset: 0,
      windowSize: 4,
      paginationFactor: 210,
      comics: []
    };
  },
  methods: {
    getComics() {
      const { ts, hash, publicKey } = getAuth();
      axios
        .get(
          `${urlAPI}comics?limit=10&ts=${ts}&apikey=${publicKey}&hash=${hash}`
        )
        .then(response => {
          this.comics = response.data.data.results;
        });
    },
    moveCarousel(direction) {
      // Find a more elegant way to express the :style. consider using props to make it truly generic
      if (direction === 1 && !this.atEndOfList) {
        this.currentOffset -= this.paginationFactor;
      } else if (direction === -1 && !this.atHeadOfList) {
        this.currentOffset += this.paginationFactor;
      }
    }
  },
  computed: {
    atEndOfList() {
      return (
        this.currentOffset <=
        this.paginationFactor * -1 * (this.comics.length - this.windowSize)
      );
    },
    atHeadOfList() {
      return this.currentOffset === 0;
    }
  },
  mounted() {
    this.getComics();
  }
};
</script>

<style scoped lang="scss">
.comics-carousel {
  display: flex;
  justify-content: center;
  align-items: center;

  &__container {
    display: flex;
    justify-content: flex-start;
    width: 840px;
    overflow: hidden;
  }

  &__cards {
    display: flex;
    transition: transform 0.8s cubic-bezier(0.175, 0.885, 0.32, 1.2);
    transform: translate(0, 0);
  }

  &__arrow {
    width: 25px;
    height: 25px;
    border-top: 3px solid red;
    border-left: 3px solid red;
    cursor: pointer;

    &--left {
      transform: rotateZ(-45deg);
    }

    &--right {
      transform: rotateZ(135deg);
    }
  }
}
</style>
