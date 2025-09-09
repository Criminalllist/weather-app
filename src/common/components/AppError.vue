<template>
  <div class="error-alert">
    <p class="error-alert__text">{{ errorMessage }}</p>
  </div>
</template>

<script setup>
defineProps({
  errorMessage: {
    type: String,
    required: true,
  },
});
</script>

<style lang="scss" scoped>
.error-alert {
  position: absolute;
  top: 0;
  left: 50%;
  translate: -50% 0;
  padding: var(--spacing-s) var(--spacing-xxl);
  background-color: var(--background-card-base);
  border-radius: 0 0 25px 25px;
  box-shadow: 1px 2px 4px 0 #222831;

  &__text {
    white-space: nowrap;
  }
}
</style>
