<template>
  <q-slide-item
    class="q-slide-item"
    left-color="green"
    right-color="red"
    @left="$emit('on_left_action')"
    @right="$emit('on_right_action')"
  >
    <q-item class="flex">
      <q-btn
        size="sm"
        round
        flat
        icon="fa-solid fa-chevron-left"
        class="qbtn success"
        @click="$emit('on_left_action')"
      />
      <div class="">{{ name }}</div>
      <q-btn
        size="sm"
        round
        flat
        icon="fa-solid fa-chevron-right"
        class="qbtn danger"
        @click="$emit('on_right_action')"
      />
    </q-item>
    <template v-slot:left> <q-icon name="done" /></template>
    <template v-slot:right><q-icon name="cancel" /></template>
  </q-slide-item>
</template>
<script setup>
import { defineProps } from "vue";

import { QBtn, QSlideItem, QItem } from "quasar"; // Slide Element
//import { QMenu, QList, QItem } from "quasar"; // menu

const props = defineProps({
  id: Number,
  name: String,
  type: String,
});
const emits = defineEmits(["on_left_action", "on_right_action"]);
const icons = {
  is_present: {
    left: "",
    right: "",
  },
  undefined: {
    left: "",
    right: "",
  },
  is_not_present: {
    left: "",
    right: "",
  },
};
</script>
<style lang="css" scoped>
.rounded {
  border: solid var(--border) 2px;
  display: flex;
  min-height: 45px;
  padding: 7px;
  width: 100%;
  margin-block: 1em;
  background-color: var(--primary);
  justify-content: space-between;
  margin-inline: auto;
}
.success {
  color: var(--success);
  border-color: var(--success);
}
.flex {
  display: flex;
  width: 100%;
  justify-content: space-between;
  height: 100%;
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
