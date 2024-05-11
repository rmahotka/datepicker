<script setup>
import { ref } from 'vue';
import ButtonItem from './UI/ButtonItem.vue';
import MonthAndYear from './MonthAndYear.vue';
import WeekItem from '@/components/WeekItem.vue';
import DayItem from '@/components/DayItem.vue';
import Arrow from '@/assets/Arrow.vue';

const props = defineProps({
  date: {
    type: Number,
  },
  location: {
    type: String,
  },
});
const getDate = new Date(props.date);
const newDate = ref();

const monthPlus = (date) => {
  newDate.value = parseInt(date.setMonth(date.getMonth() + 1));
};

const monthMinus = (date) => {
  newDate.value = parseInt(date.setMonth(date.getMonth() - 1));
};

const getDay = (day) => {
  emit('getDay', day);
};

const emit = defineEmits(['getDay']);
</script>

<template>
  <div class="widgest__block">
    <ButtonItem @click="monthMinus(getDate)">
      <Arrow />
    </ButtonItem>
    <MonthAndYear :location="location" />
    <ButtonItem @click="monthPlus(getDate)">
      <Arrow style="rotate: 180deg" />
    </ButtonItem>
  </div>
  <div>
    <WeekItem :location="props.location" />
    <DayItem :date="newDate" @get-date="getDay" />
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
