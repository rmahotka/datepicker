<script setup>
import { ref } from "vue";

const props = defineProps({
  date: {
    type: String,
    require: true,
  },
});

const getLastDayOfMonth = (year, month) => {
  let date = new Date(year, month + 1, 0);
  return date.getDate();
};
</script>

<template>
  <div></div>
</template>

<style scoped></style>
