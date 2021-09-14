<template>
  <div class="modal-container">
    <div class="modal">
      <div
        class="block w-0 bg-center bg-cover md:w-1/2"
        :style="{ 'background-image': `url(${this.result.strMealThumb})` }"
      ></div>

      <div class="w-full px-6 py-8 overflow-y-auto md:px-8 lg:w-1/2">
        <div align="right">
          <button @click="$emit('toggleModal')">
            <i class="text-4xl bi bi-x hover:text-gray-500"></i>
          </button>
        </div>
        <img
          :src="this.result.strMealThumb"
          class="block h-56 mx-auto mb-2 bg-cover rounded-md md:hidden"
        />
        <h1>{{ result.strMeal }}</h1>
        <p class="mb-3 text-sm leading-relaxed md:text-base">
          <b> Bahan :</b> <br />
          <span v-for="i in ingredients" :key="i">
            <span v-if="i"> {{ i }}, &nbsp; </span>
          </span>
        </p>
        <p class="mb-3 text-sm leading-relaxed md:text-base">
          <b>Instruksi : </b> <br />
          {{ result.strInstructions }}
        </p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "ResultModal",
  props: ["result"],
  data() {
    return {
      ingredients: [],
      ingredientsMeasure: [],
    };
  },
  mounted() {
    //  the data structure of the response we get from this api
    //  is really bad that i need to do these stupid hacks, i'm sorry :(
    for (let i = 1; i <= 20; i++) {
      let getIngredient = "this.result.strIngredient";
      let getIngredientMeasure = "this.result.strMeasure";
      getIngredient += i;
      getIngredientMeasure += i;
      this.ingredients.push(eval(getIngredient));
      this.ingredientsMeasure.push(eval(getIngredientMeasure));
    }
  },
};
</script>

<style lang="postcss" scoped>
.modal-container {
  @apply fixed inset-0 z-30 w-full h-full bg-gray-600 bg-opacity-80 p-2 md:p-10;
}
.modal {
  @apply flex lg:max-w-5xl  overflow-hidden bg-white rounded-lg shadow-lg mx-auto h-full;
}
h1 {
  @apply mb-8 text-2xl font-bold tracking-tighter text-center text-black  lg:text-left lg:text-2xl;
}
</style>
