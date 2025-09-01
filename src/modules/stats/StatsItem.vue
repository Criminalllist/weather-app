<template>
  <li class="stats-item">
    <h3 class="stats-item__title">{{ title }}</h3>
    <p class="stats-item__value">{{ value }}</p>
  </li>
</template>

<script setup>
defineProps({
  title: {
    type: String,
    required: true,
  },
  value: {
    type: String,
    required: true,
  },
});
</script>

<style lang="scss" scoped>
.stats-item {
  display: flex;
  justify-content: space-between;
  align-items: center;
  gap: var(--spacing-m);

  &__title,
  &__value {
    font-size: var(--font-size-xl);
    color: var(--color-light);
  }

  &__title {
    text-transform: uppercase;
    font-weight: var(--font-weight-bold);
  }

  &__value {
    font-weight: var(--font-weight-medium);
  }
}
</style>
