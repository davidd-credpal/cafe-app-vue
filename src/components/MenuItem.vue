<template>
  <div class="md:flex mx-10 my-4">
    <div
      v-for="item in simpleMenu"
      :key="item.name"
      class="flex-1 flex-shrink-0 flex-wrap bg-white overflow-hidden shadow-lg px-6 py-4 mx-2 my-4 "
    >
      <img
        class="menu-item__image"
        :src="item.image.source"
        :alt="item.image.alt"
      />
      <div>
        <h3 class="text-2xl">{{ item.name }}</h3>
        <p class="text-h1" v-if="item.inStock">In Stock</p>
        <p class="text-red-600" v-else>Out of Stock</p>
        <div class="my-1">
          <label for="add-item-quantity" class="mx-3"
            >Quantity: {{ item.quantity }}</label
          >
          <input
            class="bg-white focus:outline-none focus:shadow-outline border border-gray-300 rounded-lg mx-auto my-2 py-2 px-4 block appearance-none leading-normal"
            v-model.number="item.quantity"
            id="add-item-quantity"
            type="number"
          />
          <button
            class="bg-h1 hover:bg-green-900 focus:outline-none text-white font-bold py-2 px-4 mt-2 rounded"
            @click="addToShoppingCart(item.quantity)"
          >
            Add to Cart
          </button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: ["addToShoppingCartFunc"],
  data: function() {
    return {
      simpleMenu: [
        {
          name: "Crossiant",
          image: {
            source: "images/crossiant.jpg",
            alt: "A crossiant",
          },
          inStock: true,
          quantity: 1,
        },
        {
          name: "French Baguette",
          image: {
            source: "images/french-baguette.jpeg",
            alt: "Four French Baguettes",
          },
          inStock: true,
          quantity: 1,
        },
        {
          name: "Éclair",
          image: {
            source: "images/eclair.jpg",
            alt: "Chocolate Éclair",
          },
          inStock: false,
          quantity: 1,
        },
      ],
    };
  },
  methods: {
    addToShoppingCart(amount) {
      this.addToShoppingCartFunc(amount);
    },
  },
};
</script>

<style scoped>
/* .menu-item {
  display: flex;
  width: 500px;
  justify-content: space-between;
  margin-bottom: 30px;
} */

.menu-item__image {
  /* max-width: 250px; */
  height: 200px;
  min-width: 100%;
}
</style>
