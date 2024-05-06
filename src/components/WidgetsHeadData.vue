<script setup>
import { ref } from "vue";
import ButtonItem from "./UI/ButtonItem.vue";
import MonthAndYear from "./MonthAndYear.vue";

const props = defineProps({
  date: {
    type: Number,
    require: true,
  },
  location: {
    type: String,
    require: true,
  },
});

const newDate = ref();

const monthPlus = (date) => {
  newDate.value = parseInt(date.setMonth(date.getMonth() + 1));
};

const monthMinus = (date) => {
  newDate.value = date.setMonth(date.getMonth() - 1);
};
</script>

<template>
  <div class="widgest__block">
    <ButtonItem @click="monthMinus(props.date)">◀</ButtonItem>
    <MonthAndYear :date="newDate" :location="location" />
    <ButtonItem @click="monthPlus(props.date)">▶</ButtonItem>
  </div>
</template>

<style scoped>
.widgest__block {
  display: flex;
  align-items: center;
  justify-content: space-between;
  width: 100%;
}
</style>
