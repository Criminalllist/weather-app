<template>
  <main class="main">
    <h1 class="visually-hidden">Weather App</h1>
    <div class="main__container">
      <AppError v-if="isError" :error-message="errorMessage" />

      <template v-else>
        <StatsList :data="weatherStats" />
        <ForecastList :data="forecast" @set-active="setActive" />
      </template>

      <CitySelect class="main__city-select" @select-city="getWeatherData" />
    </div>
  </main>
  <SpriteLoader />
</template>

<script setup>
import { ref, computed } from "vue";
import StatsList from "@/modules/stats/StatsList.vue";
import CitySelect from "@/modules/city-select/CitySelect.vue";
import SpriteLoader from "@/common/components/SpriteLoader.vue";
import AppError from "@/common/components/AppError.vue";
import ForecastList from "@/modules/forecast/ForecastList.vue";

const API_ENDPOINT = import.meta.env.VITE_WEATHER_API_ENDPOINT;
const API_KEY = import.meta.env.VITE_WEATHER_API_KEY; // I know, it's not safe, but it's for the example

const data = ref();
const isError = ref(false);
const errorMessage = ref("");
const currentId = ref(0);

const setActive = (id) => {
  currentId.value = id;
};

const getWeatherData = async (city) => {
  if (!API_KEY || !API_ENDPOINT) {
    throw new Error("API key or endpoint is not set");
  }

  const params = new URLSearchParams({
    q: city,
    lang: "ru",
    key: API_KEY,
    days: "4",
  });

  try {
    const response = await fetch(`${API_ENDPOINT}/forecast.json?${params.toString()}`);
    if (!response.ok) {
      throw new Error("Указанный город не найден");
    }
    isError.value = false;
    data.value = await response.json();
  } catch (error) {
    isError.value = true;
    errorMessage.value = error.message;
  }
};

const weatherStats = computed(() => {
  return data.value
    ? [
        {
          label: "Влажность",
          value: `${data.value.current.humidity} %`,
        },
        {
          label: "Осадки",
          value: `${data.value.current.precip_mm} мм`,
        },
        {
          label: "Ветер",
          value: `${(data.value.current.wind_kph / 3.6).toFixed(2)} м/с`,
        },
      ]
    : [];
});

const forecast = computed(() => {
  return data.value
    ? [
        {
          id: 0,
          icon: getForecastIcon(data.value.forecast.forecastday[0].day.condition.code),
          date: new Date(data.value.forecast.forecastday[0].date),
          temp: data.value.forecast.forecastday[0].day.maxtemp_c,
          isCurrent: currentId.value === 0,
        },
        {
          id: 1,
          icon: getForecastIcon(data.value.forecast.forecastday[1].day.condition.code),
          date: new Date(data.value.forecast.forecastday[1].date),
          temp: data.value.forecast.forecastday[1].day.maxtemp_c,
          isCurrent: currentId.value === 1,
        },

        {
          id: 2,
          icon: getForecastIcon(data.value.forecast.forecastday[2].day.condition.code),
          date: new Date(data.value.forecast.forecastday[2].date),
          temp: data.value.forecast.forecastday[2].day.maxtemp_c,
          isCurrent: currentId.value === 2,
        },
        {
          id: 3,
          icon: getForecastIcon(data.value.forecast.forecastday[3].day.condition.code),
          date: new Date(data.value.forecast.forecastday[3].date),
          temp: data.value.forecast.forecastday[3].day.maxtemp_c,
          isCurrent: currentId.value === 3,
        },
      ]
    : [];
});

const getForecastIcon = (code) => {
  switch (code) {
    case 1000:
      return "sunny";
    case 1003:
      return "cloudy";
    case 1006:
      return "cloudy";
    case 1009:
      return "rainy";
    case 1195:
      return "rainy";
    case 1063:
      return "rainy";
    default:
      return "sunny";
  }
};
</script>

<style lang="scss" scoped>
.main {
  &__container {
    display: flex;
    flex-direction: column;
    position: relative;
    max-width: var(--container-max-width);
    width: 100%;
    min-height: 400px;
    padding: var(--container-padding);
    border-radius: var(--border-radius-large);
    background-color: var(--background-base);
  }

  &__city-select {
    margin-top: auto;
  }
}
</style>
