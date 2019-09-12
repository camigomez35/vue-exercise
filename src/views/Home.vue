<template>
  <div class="home">
    <StudentCard
      v-for="student of students"
      :key="student.user"
      :name="student.name"
      :user="student.user"
      :type="student.type"
    ></StudentCard>
  </div>
</template>

<script>
import StudentCard from "@/components/StudentCard.vue";

export default {
  name: "home",
  components: {
    StudentCard
  },
  data() {
    return {
      students: [
        { name: "Hanna", user: "hanna446", type: "student" },
        { name: "Frank", user: "Frankruiz90", type: "student" },
        { name: "Victor", user: "Sonny97", type: "student" },
        { name: "Jhonatan", user: "jhonatanrojasbastidas", type: "student" },
        { name: "Arley", user: "ArleyAV", type: "student" },
        { name: "Christian", user: "christiang6", type: "student" },
        { name: "Valery", user: "valuarte", type: "student" },
        { name: "Brayan", user: "brayan", type: "student" },
        { name: "Camila", user: "camigomez35", type: "teacher" },
        { name: "Juanse", user: "jsebax", type: "teacher" },
        { name: "Jose", user: "josemariogutierrez", type: "teacher" },
        { name: "Juan", user: "jusk02", type: "teacher" }
      ]
    };
  }
};
</script>
<style lang="scss">
.home {
  display: flex;
  flex-wrap: wrap;
  justify-content: space-around;
  max-width: 1280px;
  margin: 0 auto;
}
</style>
