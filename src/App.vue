<script setup>
import Calendar from "@/components/Calendar.vue";
import InputItem from "@/components/UI/InputItem.vue";

import { ref } from "vue";

const visible = ref(false);
const inputDate = ref("");
const location = ref(window.clientInformation.language);

const date = new Date();

const useVisible = () => {
  visible.value = true;
};

const dayClick = (day) => {
  const selectedDate = `${day.d}-${
    day.m + 1 < 10 ? "0" + Number(day.m + 1) : day.m + 1
  }-${day.y}`;
  inputDate.value = selectedDate;
  visible.value = false;
};
</script>

<template>
  <div class="container">
    <InputItem v-model="location" />
    <div class="block">
      <InputItem @click="useVisible" v-model="inputDate" />
      <Transition>
        <div class="block-calendar" v-if="visible">
          <Calendar :date="date" :location="location" @get-day="dayClick" />
        </div>
      </Transition>
    </div>
  </div>
</template>

<style scoped>
.container {
  height: 100vh;
  width: 100%;
  display: flex;
  align-items: center;
  justify-content: flex-start;
  flex-direction: column;
}

.block {
  margin: 0 auto;
  position: relative;
  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: column;
  width: 100%;
}

.block-calendar {
  margin-top: 3px;
  max-width: 240px;
  width: 100%;
  border: 1px solid #acacac;
  border-radius: 8px;
  padding: 10px;
  position: absolute;
  top: 100%;
}

.v-enter-active,
.v-leave-active {
  transition: opacity 0.3s ease;
}

.v-enter-from,
.v-leave-to {
  opacity: 0;
}
</style>
