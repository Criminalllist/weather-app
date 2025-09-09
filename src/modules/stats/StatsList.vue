<template>
  <section class="stats">
    <h2 class="visually-hidden">Статистика</h2>
    <ul class="stats-list">
      <StatsItem v-for="item in data" :key="item.title" v-bind="item" />
    </ul>
  </section>
</template>

<script setup>
import StatsItem from "./StatsItem.vue";

defineProps({
  data: {
    type: Array,
    required: true,
  },
});
</script>

<style lang="scss" scoped>
.stats-list {
  display: flex;
  flex-direction: column;
  gap: var(--spacing-m);
  margin-bottom: 60px;
}
</style>
