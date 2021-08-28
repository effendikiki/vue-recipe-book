<template>
  <header>
    <nav
      class="relative z-10 flex flex-wrap items-center justify-between px-5 py-2 "
    >
      <div class="flex items-center gap-2 sm:ml-12">
        <i class="bi bi-bag-fill text-primary"></i>
        <h2
          class="text-base font-medium tracking-tighter text-black sm:text-xl lg:text-x lg:mr-8"
        >
          Ricetto Collection
        </h2>
      </div>

      <a href="http://github.com/effendikiki" target="_blank">
        <button class="btn text-primary-dark">
          <i class="text-xl sm:text-3xl bi bi-github"></i>
        </button>
      </a>
    </nav>
  </header>
</template>

<script>
export default {
  name: "Header",
};
</script>

<style></style>
