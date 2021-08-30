<template>
  <main class="min-h-screen">
    <Header />
    <Hero />
    <section>
      <InputSearch @startSearch="handleSearch" />
      <ResultList ref="resultListRef" />
    </section>
  </main>
</template>

<script>
import Header from "./components/Header.vue";
import Hero from "./components/Hero.vue";
import InputSearch from "./components/InputSearch.vue";
import ResultList from "./components/result/ResultList.vue";

export default {
  name: "App",
  components: {
    Header,
    Hero,
    InputSearch,
    ResultList,
  },
  methods: {
    handleSearch(keyword) {
      this.$refs.resultListRef.startSearch(keyword);
    },
  },
};
</script>
