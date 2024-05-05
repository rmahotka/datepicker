<script setup>
import ButtonItem from "./UI/ButtonItem.vue";
import MonthAndYear from "./MonthAndYear.vue";
</script>

<template>
  <div class="widgest__block">
    <ButtonItem>◀</ButtonItem>
    <MonthAndYear />
    <ButtonItem>▶</ButtonItem>
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
