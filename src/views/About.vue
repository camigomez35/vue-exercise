<template>
  <div class="about">
    <AboutCard
      :avatar="student.avatar_url"
      :name="student.name"
      :user="student.login"
      :bio="student.bio"
      :repos="student.public_repos"
      :type="student.type"
    ></AboutCard>
  </div>
</template>

<script>
import AboutCard from "@/components/AboutCard.vue";
import axios from "axios";
import VueAxios from "vue-axios";

export default {
  name: "about",
  components: {
    AboutCard
  },
  data() {
    return {
      student: {}
    };
  },
  methods: {
    fetchUserInfo: function(user) {
      axios.get(`https://api.github.com/users/${user}`).then(
        response => {
          this.student = response.data;
          this.student.type = this.$route.params.type;
        },
        error => {
          console.log(error);
        }
      );
    }
  },
  mounted() {
    const user = this.$route.params.user;
    this.fetchUserInfo(user);
  }
};
</script>

<style lang="scss" scope>
</style>
