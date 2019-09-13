<template>
  <div class="users-list">
    <user-card
      v-for="user of users"
      :key="user.id"
      :avatar="user.avatar_url"
      :user="user.login"
    ></user-card>
  </div>
</template>

<script>
import UserCard from '@/components/UserCard.vue';

export default {
  components: {
    UserCard,
  },
  props: {
    users: Array,
  },
};
</script>

<style scoped lang="scss">
.users-list {
  display: flex;
  flex-wrap: wrap;
  justify-content: space-around;
  max-width: 1280px;
  margin: 0 auto;
}
</style>
