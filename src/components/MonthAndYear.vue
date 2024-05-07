<template>
  <div class="block">
    <span>{{ d.month }}</span
    ><span>{{ d.year }}</span>
  </div>
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

const d = computed(() => {
  let newDate = new Date(props.date);
  let objDate = {
    month: newDate.toLocaleString(props.location, { month: "long" }),
    year: newDate.getFullYear(),
  };
  return objDate;
});
</script>

<style scoped>
.block {
  font-weight: 600;
  font-size: 16px;
  display: flex;
  align-items: center;
  gap: 7px;
}
</style>
