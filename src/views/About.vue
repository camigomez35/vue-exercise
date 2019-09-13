<template>
  <div class="about">
    <about-card
      :avatar="user.avatar_url"
      :name="user.name"
      :user="user.login"
      :bio="user.bio"
      :repos="user.public_repos"
      :type="user.type"
    ></about-card>
  </div>
</template>

<script>
import axios from 'axios';
import AboutCard from '@/components/AboutCard.vue';

export default {
  components: {
    AboutCard,
  },
  data() {
    return {
      user: {},
    };
  },
  methods: {
    fetchUserInfo(user) {
      axios.get(`https://api.github.com/users/${user}`).then(
        (response) => {
          this.user = response.data;
          this.user.type = this.$route.params.type;
        },
      );
    },
  },
  mounted() {
    const { user } = this.$route.params;
    this.fetchUserInfo(user);
  },
};
</script>

<style lang="scss" scope>
</style>
