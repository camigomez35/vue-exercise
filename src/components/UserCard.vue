<template>
  <div class="user-card">
    <router-link :to="`/about/${user}`" class="user-card__link">
      <img class="user-card__avatar" :src="avatar" alt="user" />
      <div class="user-card__nickname">{{user}}</div>
    </router-link>
  </div>
</template>

<script>
export default {
  props: {
    user: String,
    avatar: String,
  },
};
</script>

<style scoped lang="scss">
.user-card {
  display: flex;
  flex-direction: column;
  justify-content: center;
  padding: 10px;
  flex: 1 20%;
  margin: 10px;
  text-align: center;
  background-color: #ff94c2;
  box-shadow: 10px 10px 8px -8px rgba(0, 0, 0, 0.5);

  &__link {
    text-decoration: none;
  }

  &__avatar {
    margin: 0 auto;
    width: 200px;
    border-radius: 50%;
  }

  &__nickname {
    padding: 5px;
    color: white;
    font-weight: bold;
  }
}
</style>
