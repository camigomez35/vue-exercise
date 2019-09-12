<template>
  <div class="student" :class="themeClass">
    <div class="student__name">{{name}}</div>
    <router-link class="student__user" :to="'/about/'+user+'/'+type">{{user}}</router-link>
  </div>
</template>

<script>
export default {
  name: "StudentCard",
  props: {
    user: String,
    name: String,
    type: String
  },
  computed: {
    themeClass() {
      return {
        "student--blue": this.type === "student",
        "student--pink": this.type === "teacher",
        "student--juan-style": this.user === "jusk02"
      };
    }
  }
};
</script>

<style scoped lang="scss">
.student {
  display: flex;
  flex-direction: column;
  justify-content: center;
  flex: 1 20%;
  margin: 10px;
  height: 20vh;
  text-align: center;
  box-shadow: 10px 10px 8px -8px rgba(0, 0, 0, 0.5);

  &__name {
    font-size: 20px;
    font-weight: bold;
  }
}
.student--pink {
  background-color: #ff94c2;
}

.student--blue {
  background-color: #6ec6ff;
}

.student--juan-style {
  background: linear-gradient(135deg, #6ec6ff 0%, rgba(255,124,216,1) 100%);
}
</style>
