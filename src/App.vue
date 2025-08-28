<template>
  <main class="main">
    <h1 class="visually-hidden">Weather App</h1>
    <div class="main__container">
      <StatsList />
      <Button>
        <template #button-icon>
          <Icon name="location" width="33" height="33" viewBox="0 0 33 33" />
        </template>
      </Button>
    </div>
  </main>
  <SpriteLoader />
</template>

<script setup>
import Button from "@/common/components/Button.vue";
import StatsList from "@/modules/stats/StatsList.vue";
import Icon from "@/common/components/Icon.vue";
import SpriteLoader from "@/common/components/SpriteLoader.vue";
</script>

<style lang="scss" scoped>
.main {
  &__container {
    max-width: var(--container-max-width);
    width: 100%;
    padding: var(--container-padding);
    border-radius: var(--border-radius-large);
    background-color: var(--background-base);
  }
}
</style>
