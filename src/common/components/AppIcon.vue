<template>
  <svg
    xmlns="http://www.w3.org/2000/svg"
    :width="width"
    :height="height"
    :viewBox="viewBox"
    :fill="fill"
  >
    <use :href="`#icon-sprite-${name}`" />
  </svg>
</template>

<script setup>
defineProps({
  name: {
    type: String,
    required: true,
  },
  width: {
    type: [String, Number],
    default: 24,
  },
  height: {
    type: [String, Number],
    default: 24,
  },
  viewBox: {
    type: String,
    default: "0 0 24 24",
  },
  fill: {
    type: String,
    default: "none",
  },
});
</script>
