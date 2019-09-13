<template>
  <div class="about-card" :class="classObject">
    <div class="about-card__user-info">
      <div class="about-card__name">{{name}}</div>
      <div class="about-card__user">{{user}}</div>
    </div>

    <div class="about-card__avatar">
      <img :src="avatar" />
    </div>
    <div class="about-card__aditional">
      <div v-if="!!bio">{{bio}}</div>
      <div v-if="!!repos">Repos: {{repos}}</div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    user: String,
    name: String,
    avatar: String,
    repos: Number,
    bio: String,
    type: String,
  },
  computed: {
    classObject() {
      return {
        'about-card--juan-style': this.user === 'jusk02',
      };
    },
  },
};
</script>

<style scoped lang="scss">
.about-card {
  display: inline-block;
  text-align: center;
  width: 350px;

  &__user-info {
    text-align: left;
    padding: 20px;
  }

  &__name {
    font-weight: bold;
    font-size: 18px;
  }

  &__user {
    font-size: 16px;
  }

  &__avatar {
    padding: 20px;
    margin: 0 auto;
  }

  &__avatar img {
    border-radius: 50%;
    width: 100%;
  }

  &__aditional {
    padding: 20px;
    color: white;
  }

  &__user-info {
    background-color: #f06292;
  }

  &__avatar {
    background-color: #ff94c2;
  }

  &__aditional {
    background-color: #ad1457;
  }

  &--blue &__user-info {
    background-color: #2196f3;
  }

  &--blue &__avatar {
    background-color: #6ec6ff;
  }

  &--blue &__aditional {
    background-color: #1565c0;
  }

  &--juan-style &__user-info {
    background: linear-gradient(135deg, #f06292 0%, #2196f3 100%);
  }

  &--juan-style &__avatar {
    background: linear-gradient(
      135deg,
      #6ec6ff 0%,
      rgba(255, 124, 216, 1) 100%
    );
  }

  &--juan-style &__aditional {
    background: linear-gradient(135deg, #ad1457 0%, #1565c0 100%);
  }
}
</style>
