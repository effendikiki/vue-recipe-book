<template>
  <div class="container">
    <div class="input-container">
      <i class="text-base text-gray-400 sm:text-lg bi bi-search"></i>
      <input
        id="pencarian"
        placeholder="Ingin masak apa hari ini?"
        type="text"
        v-model="keyword"
      />
      <button @click="handleClick" class="btn-search">Pencarian</button>
    </div>
    <div
      id="rekomendasi"
      class="pl-6 mt-5 ml-6 mr-4 text-xs text-gray-600 md:text-base sm:flex"
    >
      <span class="hidden mr-2 md:inline">Rekomendasi : </span>
      <span
        v-for="item in rekomendasi"
        :key="item"
        class="ml-2 underline cursor-pointer text-primary"
        @click="setRecommendation(item)"
      >
        {{ item }}
      </span>
    </div>
  </div>
</template>

<script>
export default {
  name: "InputSearch",
  data() {
    return {
      rekomendasi: ["Rendang", "Steak", "Salad", "Lasagna"],
      keyword: "",
    };
  },
  methods: {
    setRecommendation(item) {
      this.keyword = item;
    },
    handleClick() {
      this.$emit("startSearch", this.keyword);
    },
  },
};
</script>
<style lang="postcss" scoped>
input {
  @apply flex-grow w-full px-4 py-3 text-xs text-black bg-transparent rounded-lg sm:text-base lg:w-auto focus:outline-none;
}

.container {
  @apply relative z-20 w-5/6 py-6 mx-auto -mt-16 bg-white rounded-lg shadow-lg  md:mx-0 md:ml-20 lg:w-2/3;
}

.input-container {
  @apply flex flex-row items-center gap-2 pl-3 ml-6 mr-4 bg-gray-100 rounded-tr-lg rounded-br-lg  sm:pl-6;
}
</style>
