<template>
  <li class="forecast-item" :class="{ active: isCurrent }">
    <button class="forecast-item__button" @click="setActive">
      <span class="forecast-item__icon">
        <AppIcon :name="icon" width="55" height="55" viewBox="0 0 55 55" />
      </span>
      <p class="forecast-item__day">
        {{ date.toLocaleDateString("ru-RU", { weekday: "short" }) }}
      </p>
      <p class="forecast-item__temp">{{ temp }} °C</p>
    </button>
  </li>
</template>

<script setup>
import AppIcon from "@/common/components/AppIcon.vue";
const props = defineProps({
  icon: {
    type: String,
    required: true,
  },
  date: {
    type: Date,
    required: true,
  },
  temp: {
    type: [String, Number],
    required: true,
  },
  isCurrent: {
    type: Boolean,
    required: true,
  },
  id: {
    type: Number,
    required: true,
  },
});

const emits = defineEmits(["set-active"]);

const setActive = () => {
  emits("set-active", props.id);
};
</script>

<style lang="scss" scoped>
.forecast-item {
  list-style: none;
  background-color: var(--background-card-base);
  border-radius: var(--border-radius-medium);
  color: var(--color-light);
  transition: background-color 0.3s ease, color 0.3s ease;

  @media (hover: hover) {
    &:hover {
      background-color: var(--background-card-hover);
    }
  }

  @media (hover: none) {
    &:active {
      background-color: var(--background-card-hover);
    }
  }

  &.active {
    background-color: var(--color-light);
    color: var(--color-dark);
  }

  &__button {
    display: flex;
    flex-direction: column;
    gap: 15px;
    min-width: 110px;
    min-height: 170px;
    padding: 15px 25px;
    border: none;
    background-color: unset;
    cursor: pointer;
  }
  &__icon {
    display: flex;
    justify-content: center;
    align-items: center;
  }

  &__day,
  &__temp {
    font-size: var(--font-size-m);
  }

  &__temp {
    font-weight: var(--font-weight-bold);
  }
}
</style>
