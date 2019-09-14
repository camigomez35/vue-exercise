<template>
  <div id="app">
    <navbar></navbar>
    <div class="container">
      <keep-alive include="home">
        <router-view/>
      </keep-alive>
    </div>
  </div>
</template>

<script>
import Navbar from '@/components/Navbar.vue'
export default {
  components: {
    Navbar
  }
}
</script>

<style lang="scss">
* {
  padding: 0;
  margin: 0;
}

#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  color: white;
}

.container {
  background: #2c3e50;
  padding: 10px 50px;
}
</style>
