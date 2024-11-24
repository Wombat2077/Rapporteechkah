<template>
  <div
    class="rounded"
    v-touch-swipe.left="$emit('on_left_action')"
    v-touch-swipe.right="'on_right_action'"
  >
    <q-btn
      size="sm"
      round
      flat
      icon="fa-solid fa-chevron-left"
      class="qbtn success"
      @click="$emit('on_left_action')"
    />
    <div class="">{{ student.name }}</div>
    <q-btn
      size="sm"
      round
      flat
      icon="fa-solid fa-chevron-right"
      class="qbtn danger"
      @click="$emit('on_right_action')"
    />
  </div>
</template>
<script setup>
import { defineProps } from "vue";
import { QBtn } from "quasar";
//import { QMenu, QList, QItem } from "quasar"; // menu

const props = defineProps({
  student: Object,
  type: String,
});
const emits = defineEmits(["on_left_action", "on_right_action"]);
const icons = {
  are_present: {
    left: "",
    right: "",
  },
  undefined: {
    left: "",
    right: "",
  },
  arent_present: {
    left: "",
    right: "",
  },
};
</script>
<style lang="css" scoped>
.rounded {
  border: solid var(--border) 2px;
  border-radius: 10px;
  display: flex;
  min-height: 45px;
  padding: 7px;
  max-width: 60%;
  margin-block: 1em;
  background-color: var(--primary);
  justify-content: space-between;
  margin-inline: auto;
}
.success {
  color: var(--success);
  border-color: var(--success);
}
.danger {
  color: var(--danger);
  border-color: var(--danger);
}
.qbtn {
  border-width: 2px;
  border-style: solid;
  border-radius: 50%;
}
</style>
