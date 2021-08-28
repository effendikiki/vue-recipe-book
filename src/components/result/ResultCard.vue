<template>
  <div class="card-container">
    <div class="card">
      <div>
        <img
          :src="result.strMealThumb"
          alt="preview"
          class="object-cover object-center w-full max-h-52"
        />
      </div>
      <div class="card-body">
        <h2 class="text-white badge bg-primary">{{ result.strCategory }}</h2>
        <h4 class="card-body-title">{{ result.strMeal }}</h4>
        <p class="mb-1 text-base leading-relaxed line-clamp-3">Instruksi :</p>
        <p class="mb-3 text-base leading-relaxed line-clamp-3">
          {{ result.strInstructions }}
        </p>

        <button
          id="triggerModal-${this._recipe.idMeal}"
          class="btn hover:bg-primary text-primary-dark"
        >
          Lihat detail
        </button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: ["result"],
};
</script>

<style lang="postcss" scoped>
.card-container {
  @apply w-full px-2 my-4 sm:w-1/2 lg:w-1/3 sm:min-w-[300px] max-w-[350px];
}
.card {
  @apply overflow-hidden bg-white border rounded-lg hover:drop-shadow-md;
}

.card-body {
  @apply flex flex-col p-6;
}

.card-body-title {
  @apply mb-4 text-2xl font-semibold tracking-tighter text-black capitalize line-clamp-1 lg:text-3xl;
}
</style>
