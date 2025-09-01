<template>
  <div class="city-select">
    <AppButton class="city-select__button" @click="changeCity">
      <template #button-icon>
        <Icon name="location" width="33" height="33" viewBox="0 0 33 33" />
      </template>
      Изменить город
    </AppButton>

    <div class="city-select__field">
      <AppInput placeholder="Введите город" />
      <AppButton @click="selectCity" />
    </div>
  </div>
  {{ isEdited }}
</template>

<script setup>
import { ref } from "vue";
import AppInput from "@/common/components/AppInput.vue";
import AppButton from "@/common/components/AppButton.vue";
import Icon from "@/common/components/AppIcon.vue";

const emits = defineEmits(["select-city"]);
let isEdited = ref(false);

const changeCity = () => {
  isEdited.value = true;
};

const selectCity = () => {
  isEdited.value = false;
  emits("select-city", "moscow");
};
</script>

<style lang="scss" scoped>
.city-select {
  &__button {
    display: flex;
    justify-content: center;
    align-items: center;
    width: 100%;
  }

  &__field {
    display: flex;
    align-items: center;
    gap: var(--spacing-m);
  }
}
</style>
