<template>
  <section class="stats">
    <h2 class="visually-hidden">Статистика</h2>
    <ul class="stats-list">
      <StatsItem v-for="{ title, value } in items" :key="title" :title :value />
    </ul>
  </section>
</template>

<script setup>
import StatsItem from "./StatsItem.vue";

const items = [
  {
    title: "Влажность",
    value: "90%",
  },
  {
    title: "Осадки",
    value: "20 мм",
  },

  {
    title: "Ветер",
    value: "10 м/с",
  },
];
</script>

<style lang="scss" scoped>
.stats-list {
  display: flex;
  flex-direction: column;
  gap: var(--spacing-m);
}
</style>
