<template>
  <button class="button" type="button">
    <span class="button__icon">
      <slot name="button-icon" />
    </span>
    <slot>Сохранить</slot>
  </button>
</template>

<script setup></script>

<style lang="scss" scoped>
.button {
  display: flex;
  align-items: center;
  gap: var(--spacing-xs);
  padding: var(--spacing-s);

  color: var(--color-light);
  font-size: var(--font-size-base);
  font-weight: var(--font-weight-semibold);
  background-image: var(--gradient-base);
  border-radius: var(--border-radius-medium);
  transition: background-image 0.3s ease;
  cursor: pointer;

  @media (hover: hover) {
    &:hover {
      background-image: var(--gradient-hover);
    }
  }

  @media (hover: none) {
    &:active {
      background-image: var(--gradient-hover);
    }
  }
}
</style>
