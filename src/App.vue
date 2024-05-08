<script setup>
import WidgetData from '@/components/WidgetData.vue';
import InputItem from '@/components/UI/InputItem.vue';

import { ref } from 'vue';

const visible = ref(false);
const location = ref('ru');

const useVisible = () => {
  visible.value = !visible.value;
};

const date = new Date();
</script>

<template>
  <div class="container">
    <InputItem @click="useVisible" />
    <div class="block" v-if="visible">
      <WidgetData :date="date" :location="location" />
    </div>
  </div>
</template>

<style scoped>
.container {
  height: 100vh;
  width: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: column;
}

.block {
  margin-top: 3px;
  max-width: 210px;
  width: 100%;
  border: 1px solid #acacac;
  border-radius: 8px;
  padding: 10px;
}
</style>
