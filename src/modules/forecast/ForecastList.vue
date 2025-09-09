<template>
  <section class="forecast">
    <ul class="forecast__list">
      <ForecastItem
        v-for="item in data"
        :key="item.date"
        v-bind="item"
        @set-active="setActive"
      />
    </ul>
  </section>
</template>

<script setup>
import ForecastItem from "./ForecastItem.vue";
defineProps({
  data: {
    type: Array,
    required: true,
  },
});

const emits = defineEmits(["set-active"]);

const setActive = (id) => {
  emits("set-active", id);
};
</script>

<style lang="scss" scoped>
.forecast {
  &__list {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    column-gap: 1px;
    margin-bottom: 70px;
  }
}
</style>
