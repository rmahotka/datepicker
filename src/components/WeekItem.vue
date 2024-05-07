<script setup>
const weekItem = ["Пн", "Вт", "Ср", "Чт", "Пт", "Сб", "Вс"];
</script>

<template>
  <div class="week-block">
    <div v-for="(item, i) of weekItem" :key="i">
      <span>{{ item }}</span>
    </div>
  </div>
</template>

<style scoped>
.week-block {
  display: grid;
  grid-template-columns: repeat(7, 1fr);
  justify-items: center;
  font-size: 16px;
  font-weight: 600;
  margin-bottom: 7px;
}
</style>
