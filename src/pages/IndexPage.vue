<template class="page">
  <q-tabs v-model="tab" no-caps class="text-teal">
    <q-tab label="Отсутствующие" name="is-not-present" />
    <q-tab label="Неназначенные" :name="'undefined'" />
    <q-tab label="Присутствующие" name="is-present" />
  </q-tabs>

  <div v-for="item of current_list" :key="item.id">
    <StudentCard
      :name="item.name"
      @on_left_action="onLeft(item)"
      @on_right_action="onRight(item)"
    />
  </div>
</template>

<script setup>
import { computed, ref, reactive, onMounted } from "vue";
import StudentCard from "src/components/StudentCard.vue";

const students = reactive([
  {
    id: 1,
    name: "Андреев Сергей",
    status: "undefined",
  },
  {
    id: 2,
    name: "Бобровский Кирилл",
    status: "undefined",
  },
  {
    id: 3,
    name: "Владимиров Захар",
    status: "undefined",
  },
  {
    id: 4,
    name: "",
  },
]);
var i = 0; //update i
const tab = ref("undefined");

function onRight(value) {
  value.status = "is-not-present";
  i++;
}

function onLeft(value) {
  value.status = "is-present";
  i--;
}
const current_list = computed(() => {
  i;
  return students.filter((i) => i.status == tab.value);
});
onMounted(() => {});
console.log(current_list);
</script>
<style lang="css" scoped>
.page {
  display: flex;
  flex-direction: column;
}
</style>
