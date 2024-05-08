<script setup>
import { ref, computed } from 'vue';

const props = defineProps({
  date: {
    type: Number,
    require: true,
    default: new Date(),
  },
});

const dayNowClass = ref('dayNow');
const dayNow = new Date();

const getLastDayOfMonth = (year, month) => {
  let date = new Date(year, month + 1, 0);
  return date.getDate();
};

const d = computed(() => {
  let date = new Date(props.date);
  return getLastDayOfMonth(date.getFullYear(), date.getMonth());
});
</script>

<template>
  <div class="number-block">
    <div
      class="number-item"
      :class="item === dayNow.getDate() ? dayNowClass : ''"
      v-for="(item, index) in d"
      :key="index"
    >
      <span>
        {{ item }}
      </span>
    </div>
  </div>
</template>

<style scoped>
.number-block {
  display: grid;
  justify-items: center;
  grid-template-columns: repeat(7, 1fr);
}

.number-item {
  grid-column: 1 span;
  cursor: pointer;
  display: flex;
  align-items: center;
  justify-content: center;
  border-radius: 50%;
  width: 100%;
  height: 22px;
  padding: 4px 0;
}

.number-item:hover {
  transition: 0.15s;
  background-color: #e9cfcf;
}

.dayNow {
  background-color: #ececec;
}
</style>
