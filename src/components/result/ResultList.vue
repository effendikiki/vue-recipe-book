<template>
  <div class="px-5 py-16 mx-auto bg-white lg:px-28 ">
    <h1 v-if="resultMessage">
      {{ resultMessage }}
    </h1>
    <h1 v-if="isLoading">Loading . . .</h1>
    <div
      v-if="results"
      class="flex flex-wrap items-start justify-center mb-16 lg:justify-start xl:mr-10 md:pr-12 md:mb-0"
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

<script>
import axios from "axios";
import ResultCard from "./ResultCard.vue";

export default {
  name: "ResultList",
  components: { ResultCard },
  data() {
    return {
      resultMessage: "",
      results: [],
      isLoading: null,
    };
  },
  methods: {
    startSearch(keyword) {
      this.isLoading = true;
      this.resultMessage = "";
      axios
        .get(`https://www.themealdb.com/api/json/v1/1/search.php?s=${keyword}`)
        .then((response) => {
          this.renderResult(response.data.meals, keyword);
          this.isLoading = false;
        })
        .catch((error) => console.log(error));
    },
    renderResult(results, keyword) {
      if (results) {
        this.resultMessage = `${results.length} hasil pencarian untuk "${keyword}"`;
        this.results = results;
      } else {
        this.resultMessage = `Pencarian ${keyword} Tidak ditemukan`;
        this.results = "";
      }
    },
  },
};
</script>

<style lang="postcss" scoped>
h1 {
  @apply mb-8 text-2xl font-bold tracking-tighter text-center text-black  lg:text-left lg:text-2xl;
}
</style>
