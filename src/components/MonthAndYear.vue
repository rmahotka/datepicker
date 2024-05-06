<template>
  <div>{{ d }}</div>
</template>

<script setup>
import { computed } from "vue";

const props = defineProps({
  date: {
    type: Number,
    require: true,
    default: new Date(),
  },
  location: {
    type: String,
    require: true,
  },
});

const option = {
  year: "numeric",
  month: "long",
};

const d = computed(() => {
  return new Date(props.date).toLocaleString(props.location, option);
});
</script>

<style scoped></style>
