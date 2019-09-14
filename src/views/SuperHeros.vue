<template>
  <div class="heros">
    <h1 class="heros__title">Heros</h1>
    <heros-list></heros-list>
  </div>
</template>

<script>
import HerosList from "@/components/HerosList.vue";

export default {
  components: {
    HerosList
  }
};
</script>
<style lang="scss">
.heros {

  &__title {
    padding: 0 10px;
  }
}
</style>
