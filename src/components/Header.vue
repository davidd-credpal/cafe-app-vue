<template>
  <div>
    <header
      class="flex flex-row flex-wrap items-center justify-between px-4 py-4 bg-red-800 w-full text-white fixed"
    >
      <div class="sm:mx-0 lg:mx-16">
        <h3 class="font-semibold">Call Us: {{ phone }}</h3>
      </div>
      <div>
        
      </div>
      <div class="sm:mx-0 lg:mx-16 items-center">
        <aside>
          <h2 class="text-white font-semibold">
            Shopping Cart: {{ shoppingCart }} items
          </h2>
        </aside>
      </div>
    </header>
  </div>
</template>

<script>
export default {
  props: ["phone", "shoppingCart"],
};
</script>

<style scoped>
@media only screen and (max-width: 768px) {}
</style>
