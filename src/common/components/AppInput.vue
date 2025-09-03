<template>
  <input v-model="modelValue" class="app-input" :type="type" :placeholder="placeholder" />
</template>

<script setup>
defineProps({
  type: {
    type: String,
    default: "text",
  },
  placeholder: {
    type: String,
    default: "",
  },
});

const modelValue = defineModel({ type: String, required: true });
</script>

<style lang="scss" scoped>
.app-input {
  width: 100%;
  height: 53px;
  padding: var(--spacing-xs) var(--spacing-s);
  color: var(--color-light);
  font-size: var(--font-size-m);
  background-color: var(--background-card-base);
  border-radius: var(--border-radius-medium);
  box-shadow: 1px 2px 4px 0 #222831;

  &::placeholder {
    color: var(--color-secondary);
  }

  &:focus-visible {
    outline: 1px solid var(--color-light);
    outline-offset: -1px;
  }
}
</style>
