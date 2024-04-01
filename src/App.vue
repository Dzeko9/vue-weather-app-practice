<script setup>
import Navbar from "./components/Navbar.vue";
import MainComp from "./components/MainComp.vue";
import About from "./components/About.vue";
import { ref, onMounted } from "vue";
import { useStore } from "vuex";

const store = useStore();

// 앱이 실행되면 날씨 데이터 가져오기
onMounted(() => {
  store.dispatch("getWeather");
});

const onSearchCity = (city) => {
  weatherData.value.city = city;
  getWeather;
};
</script>

<template>
  <!-- <button @click="$store.dispatch('getWeather')">getWeather</button> -->
  <Navbar />
  <div v-if="!$store.state.toggle">
    <MainComp />
  </div>
  <div v-else>
    <About />
  </div>
</template>

<!-- scoped : 컴포넌트 안에서만 스타일이 적용될 수 있도록 함 -->
<style scoped lang="scss"></style>
