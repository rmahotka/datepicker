<script setup>
import WidgetsHeadData from "./components/WidgetsHeadData.vue";
import InputItem from "./components/UI/InputItem.vue";
import { ref } from "vue";

const visible = ref(false);

const useVisible = () => {
  visible.value = !visible.value;
};
</script>

<template>
  <div class="container">
    <InputItem @click="useVisible" />
    <div class="block" v-if="visible">
      <WidgetsHeadData />
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
  max-width: 200px;
  width: 100%;
  border: 1px solid;
  border-radius: 8px;
  padding: 5px;
}
</style>
