<template>
  <time :datetime="date">{{ date }}</time>
</template>

<script setup>

const date = new Date().toLocaleDateString();

</script>

<style lang="scss" scoped></style>
