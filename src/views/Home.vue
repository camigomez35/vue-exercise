<template>
  <div class="home">
    <div class="form">
      <label class="form__label">Nickname</label>
      <input
        class="form__input"
        placeholder="Write here..."
        type="text"
        v-model="user"
        @keyup="debounceFunc" />
    </div>
    <users-list :users="users"></users-list>
  </div>
</template>

<script>
import axios from 'axios';
import UsersList from '@/components/UsersList.vue';

export default {
  name: 'home',
  components: {
    UsersList,
  },
  data() {
    return {
      user: '',
      users: [],
    };
  },
  methods: {
    debounce(func, wait) {
      let timeout;
      return () => {
        clearTimeout(timeout);
        timeout = setTimeout(() => func(), wait);
      };
    },
    getUsers() {
      if (this.user.length) {
        axios
          .get(`https://api.github.com/search/users?per_page=8&q=${this.user}`)
          .then((response) => {
            this.users = response.data.items;
          });
      } else {
        this.users = [];
      }
    },
  },
  computed: {
    debounceFunc() { return this.debounce(this.getUsers, 500); },
  },
};
</script>
<style lang="scss">
.form {
  display: flex;
  flex-direction: column;
  justify-content: flex-start;
  text-align: start;
  max-width: 600px;
  margin: 0 auto;
}

.form__label {
  margin: 0 5px;
}

.form__input {
  width: 100%;
  padding: 10px 22px;
  margin: 10px 5px;
  box-sizing: border-box;
}
</style>
