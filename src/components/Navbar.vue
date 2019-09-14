<template>
  <div class="nav">
    <router-link to="/">Home</router-link>
    <router-link to="/heros">Heros</router-link>
  </div>
</template>

<script>

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
.nav {
  padding: 30px;
  background: black;
  a {
    font-weight: bold;
    color: white;
    &.router-link-exact-active {
      color: #5bf3ae;
    }
  }
}
</style>
