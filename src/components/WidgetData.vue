<script setup>
import { ref } from "vue";
import ButtonItem from "./UI/ButtonItem.vue";
import MonthAndYear from "./MonthAndYear.vue";
import WeekItem from "@/components/WeekItem.vue";
import DayItem from "@/components/DayItem.vue";
import arrowLeft from "@/assets/arrowLeft.vue";
import arrowRigth from "@/assets/arrowRigth.vue";

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
  newDate.value = parseInt(date.setMonth(date.getMonth() - 1));
};
</script>

<!-- П\сделать одну стрелку со стилями -->
<template>
  <div class="widgest__block">
    <ButtonItem @click="monthMinus(props.date)">
      <arrowLeft />
    </ButtonItem>
    <MonthAndYear :date="newDate" :location="location" />
    <ButtonItem @click="monthPlus(props.date)">
      <arrowRigth />
    </ButtonItem>
  </div>
  <div>
    <WeekItem />
    <DayItem :date="newDate" />
  </div>
</template>

<style scoped>
.widgest__block {
  display: flex;
  align-items: center;
  justify-content: space-between;
  width: 100%;
  border-bottom: 1px solid #acacac;
  padding-bottom: 7px;
  margin-bottom: 15px;
}
</style>
