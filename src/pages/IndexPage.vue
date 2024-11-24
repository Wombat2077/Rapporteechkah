<template class="page">
  <StudentCard
    v-for="student of students"
    :student="student"
    :key="student.id"
  />
</template>

<script setup>
import { ref } from "vue";
import StudentCard from "src/components/StudentCard.vue";
//

const students = ref([
  {
    id: 1,
    name: "Андреев Сергей",
  },
  {
    id: 2,
    name: "Бобровский Кирилл",
  },
  {
    id: 3,
    name: "Владимиров Захар",
  },
]);
</script>
<style lang="css" scoped>
.page {
  display: flex;
  flex-direction: column;
}
</style>
