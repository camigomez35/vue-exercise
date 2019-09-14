<template>
  <div class="hero-card" @click="descriptionEvent" :class="{'hero-card--show-description': showDescription}">
    <div class="hero-card__info">
      <div class="hero-card__avatar">
        <img class="hero-card__avatar-img" :src="thumbnail" alt="name" />
      </div>
      <div class="hero-card__nickname-container">
        <div class="hero-card__nickname">{{name}}</div>
      </div>
    </div>
    <div class="hero-card__description">
      <div v-if="description" class="hero-card__description-text">
        {{description}}
      </div>
      <div v-else class="hero-card__description-text">
        Info not found
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      showDescription: false
    }
  },
  props: {
    name: String,
    thumbnail: String,
    description: String,
  },
  methods: {
    descriptionEvent() {
      this.showDescription = !this.showDescription;
    }
  }
};
</script>

<style scoped lang="scss">
.hero-card {
  position: relative;
  display: flex;
  flex-direction: column;
  justify-content: flex-start;
  margin: 5px;
  width: 200px;
  cursor: pointer;
  transform-style: preserve-3d;

  &__info {
    transition: transform 2s;
    backface-visibility: hidden;
  }

  &__avatar {
    margin: 0 auto;
    height: 200px;
    border-bottom: 5px solid red;
  }

  &__avatar-img {
    height: 100%;
    width: 100%;
    object-fit: cover;
  }

  &__nickname-container {
    display: inline-block;
    position: relative;
    padding: 5px 0;
    color: white;
    font-weight: bold;
    background: black;
    width: 100%;
    text-align: center;
  }

  &__nickname {
    position: relative;
  }

  &__nickname-container::before {
    content: "";
    position: absolute;
    background: red;
    height: 100%;
    transform: scaleY(0);
    transform-origin: top;
    top: 0;
    left: 0;
    transition: transform 0.3s;
    width: 100%;
  }

  &:hover &__nickname-container::before {
    transform: scaleY(1);
  }

  &__description {
    display: flex;
    align-items: center;
    position: absolute;
    height: 100%;
    width: 100%;
    font-size: 14px;
    background: black;
    text-align: center;
    transition: transform 2s;
    backface-visibility: hidden;
    transform: rotateY(180deg);
  }

  &--show-description &__info {
    transform: rotateY(180deg);
  }

  &--show-description &__description {
    transform: rotateY(0deg);
  }

  &__description-text {
    padding: 5px;
    width: 100%;
  }
}
</style>
