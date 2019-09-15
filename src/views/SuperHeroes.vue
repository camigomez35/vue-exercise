<template>
  <div class="heroes">
    <h1 class="heroes__title">Heroes</h1>
    <heroes-list></heroes-list>
  </div>
</template>

<script>
import heroesList from "@/components/HeroesList.vue";

export default {
  components: {
    heroesList
  }
};
</script>
<style lang="scss">
.heroes {

  &__title {
    padding: 0 10px;
  }
}
</style>
