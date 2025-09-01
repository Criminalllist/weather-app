<template>
  <main class="main">
    <h1 class="visually-hidden">Weather App</h1>
    <div class="main__container">
      <StatsList />

      <CitySelect />
    </div>
  </main>
  <SpriteLoader />
</template>

<script setup>
import StatsList from "@/modules/stats/StatsList.vue";
import CitySelect from "@/modules/city-select/CitySelect.vue";
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
