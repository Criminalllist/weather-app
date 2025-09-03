<template>
  <section class="stats">
    <h2 class="visually-hidden">Статистика</h2>
    <ul class="stats-list">
      <StatsItem v-for="item in modifiedData" :key="item.title" v-bind="item" />
    </ul>
  </section>
</template>

<script setup>
import { ref, computed } from "vue";
import StatsItem from "./StatsItem.vue";

let data = ref({
  humidity: 90,
  precipitation: 20,
  wind: 10,
});

const modifiedData = computed(() => {
  return [
    {
      label: "Влажность",
      value: `${data.value.humidity} %`,
    },
    {
      label: "Осадки",
      value: `${data.value.precipitation} мм`,
    },
    {
      label: "Ветер",
      value: `${data.value.wind} м/с`,
    },
  ];
});
</script>

<style lang="scss" scoped>
.stats-list {
  display: flex;
  flex-direction: column;
  gap: var(--spacing-m);
}
</style>
