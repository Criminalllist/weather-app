<template>
  <section class="city-select">
    <AppButton v-if="!isEdited" class="city-select__button" @click="changeCity">
      <template #button-icon>
        <Icon name="location" width="33" height="33" viewBox="0 0 33 33" />
      </template>
      Изменить город
    </AppButton>

    <div v-else class="city-select__field">
      <AppInput
        v-model="currentCity"
        placeholder="Введите город"
        @keyup.enter="selectCity"
      />
      <AppButton @click="selectCity" />
    </div>
  </section>
</template>

<script setup>
import { ref, onMounted } from "vue";
import AppInput from "@/common/components/AppInput.vue";
import AppButton from "@/common/components/AppButton.vue";
import Icon from "@/common/components/AppIcon.vue";

const emits = defineEmits(["select-city"]);

const isEdited = ref(false);
const currentCity = ref("");

const changeCity = () => {
  isEdited.value = true;
};

onMounted(() => {
  emits("select-city", "Москва");
});

const selectCity = async () => {
  emits("select-city", currentCity.value);
  isEdited.value = false;
};
</script>

<style lang="scss" scoped>
.city-select {
  min-width: 420px;
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
