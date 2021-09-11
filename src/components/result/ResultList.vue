<template>
  <div class="px-5 py-16 mx-auto bg-white lg:px-28">
    <h1 v-if="resultMessage">
      {{ resultMessage }}
    </h1>
    <h1 v-if="isLoading">Loading . . .</h1>
    <div
      v-if="results"
      class="flex flex-wrap items-start justify-center mb-16  lg:justify-start xl:mr-10 md:pr-12 md:mb-0"
    >
      <ResultCard
        v-for="result in results"
        :key="result.idMeal"
        :result="result"
      >
        {{ result.strMeal }},
      </ResultCard>
    </div>
  </div>
</template>

<script setup>
import axios from "axios";
import ResultCard from "./ResultCard.vue";
import { ref } from "@vue/reactivity";

const resultMessage = ref("");
const results = ref(null);
const isLoading = ref(null);

const startSearch = (keyword) => {
  isLoading.value = true;
  resultMessage.value = "";
  axios
    .get(`https://www.themealdb.com/api/json/v1/1/search.php?s=${keyword}`)
    .then((response) => {
      renderResult(response.data.meals, keyword);
      isLoading.value = false;
    })
    .catch((error) => console.log(error));
};

const renderResult = (response, keyword) => {
  if (response) {
    resultMessage.value = `${response.length} hasil pencarian untuk "${keyword}"`;
    results.value = response;
  } else {
    resultMessage.value = `Pencarian ${keyword} Tidak ditemukan`;
    results.value = "";
  }
};

defineExpose({ startSearch });
</script>

<style lang="postcss" scoped>
h1 {
  @apply mb-8 text-2xl font-bold tracking-tighter text-center text-black  lg:text-left lg:text-2xl;
}
</style>
