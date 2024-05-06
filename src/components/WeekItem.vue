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
  display: flex;
  justify-content: space-between;
  font-size: 12px;
  margin: 3px 0;
}
</style>
