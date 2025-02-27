<template>
  <div v-if="$store.state.weatherData.icon === 'icon'">
    로딩중...
  </div>
  <div class="weather-info" v-else>
    <div class="icon">
      <img :src="`https://openweathermap.org/img/wn/${$store.state.weatherData.icon}@2x.png`" :alt="$store.state.weatherData.icon">
    </div>
    <div class="temp">{{ temperatureCelsius.toFixed(2) }}&deg;</div>
    <div class="text">{{ $store.state.weatherData.text }}</div>
    <div class="location">{{ $store.state.weatherData.city }},{{ $store.state.weatherData.location }}</div>
  </div>
</template>

<script setup>
  import { computed } from 'vue';
  import { useStore } from 'vuex';

  const store = useStore();

  const temperatureCelsius = computed(() => store.state.weatherData.temp - 273.15);

</script>

<style lang="scss" scoped>
  .weather-info {
    padding: 20px;
    & > div {
      margin-bottom: 20px;
      padding: 20px;
      border: 1px solid #ccc;
    }
    .icon img {
      width: 140px;
    }
    .temp {
      font-size: 4em;
    }
    .text {
      font-size: 2em;
    }
  }
</style>