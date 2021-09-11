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

<script setup>
import { ref } from "@vue/reactivity";
import Header from "./components/Header.vue";
import Hero from "./components/Hero.vue";
import InputSearch from "./components/InputSearch.vue";
import ResultList from "./components/result/ResultList.vue";

const resultListRef = ref(null);

const handleSearch = (keyword) => {
  resultListRef.value.startSearch(keyword);
};
</script>
