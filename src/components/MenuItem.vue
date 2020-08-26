<template>
    <div
      class="flex-1 flex-shrink-0 flex-wrap bg-white overflow-hidden shadow-lg px-6 py-4 mx-2 my-4 "
    >
      <img class="menu-item__image" :src="image.source" :alt="image.alt" />
      <div>
        <h3 class="text-2xl">{{ name }}</h3>
        <p class=" font-semibold tracking-wider text-gray-800">
          Price: {{ price }}
        </p>
        <p class="text-h1" v-if="inStock">In Stock</p>
        <p class="text-red-600" v-else>Out of Stock</p>
        <div class="my-1">
          <label for="add-item-quantity" class="mx-3"
            >Quantity: {{ quantity }}</label
          >
          <input
            class="bg-white focus:outline-none focus:shadow-outline border border-gray-300 rounded-lg mx-auto my-2 py-2 px-4 block appearance-none leading-normal"
            v-model.number="quantity"
            id="add-item-quantity"
            type="number"
          />
          <button
            class="bg-h1 hover:bg-green-900 focus:outline-none text-white font-bold py-2 px-4 mt-2 rounded"
            @click="addToShoppingCart(quantity)"
          >
            Add to Cart
          </button>
          
        </div>
      </div>
    </div>
  
</template>

<script>
export default {
  props: ["addToShoppingCart", "image", "inStock", "name", "price", "quantity"],
  beforeMount() {
    var day = new Date().getDay();
    var discount = 0.1;
    var price = this.price;
    var discountedPrice = this.price - discount * this.price;
    console.log(discountedPrice);
    if (day % 2 === 0) {
      this.price = discountedPrice.toFixed(2);
    } else {
      this.price = price;
    }
  },
};
</script>
<style scoped>


.menu-item__image {
  /* max-width: 250px; */
  height: 200px;
  min-width: 100%;
}
</style>
