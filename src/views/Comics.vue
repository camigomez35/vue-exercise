<template>
  <div class="comics">
    <h1 class="heroes__title">Comics</h1>
    <comics-carousel></comics-carousel>
  </div>
</template>

<script>
import ComicsCarousel from "@/components/ComicsCarousel.vue";

export default {
  components: {
    ComicsCarousel
  }
};
</script>
<style lang="scss">
.comics {
  position: relative;
  width: 100%;
  height: 100%;
}
</style>
