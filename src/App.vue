<template>
  <div
    id="app"
    class="lg:container lg:mx-auto h-full bg-green-100 w-full antialiased"
  >
    <Header :phone="phone" :shoppingCart="shoppingCart" />
    <div class="justify-center">
      <img
        class="w-full bg-no-repeat bg-center bg-cover object-cover relative"
        :src="backgroundImage.headerImage"
        :alt="backgroundImage.altHeaderImage"
      />
      <div class="imagetextcenter w-full">
        <h1
          class="text-center font-semibold text-white text-5xl lg:text-6xl"
          v-html="restaurantNameHeader"
        ></h1>
        <!-- <div class="sm:hidden lg:block">
          <h5 class="text-5xl text-red-900 font-semibold">Food is Life</h5>
        </div> -->
      </div>
    </div>
    <div class="bg-bggreen md:mt-20 md:mb-16 p-5">
      <p class="description text-center align-middle">
        Welcome to
        <span class="font-extrabold text-2xl">{{ restaurantName }}!</span> We
        are known for our freshly baked bread and french pastries! Give you
        morning a warm start or treat yourself in the middle of the day. Our
        butter is imported from local farmers in France. Once you take your
        first bite, you will see why everyone can't get enough!
      </p>
    </div>
    <section class="menu mt-6">
      <h2 class="text-4xl text-center uppercase font-semibold text-h1">
        Menu
      </h2>
      <h4 class="text-gray-700 font-semibold capitalize tracking-widest">
        Enjoy 10% Discount Every Even day of the week
      </h4>
      <!-- menuitem component -->
      <!-- <menuItem :addToShoppingCartFunc="addToShoppingCart" /> -->
      <div class="md:flex mx-10 my-4">
        <menuItem
          v-for="item in simpleMenu"
          :addToShoppingCart="addToShoppingCart"
          :name="item.name"
          :image="item.image"
          :price="item.price"
          :quantity="item.quantity"
          :inStock="item.inStock"
          :day="day"
          :discountedPrice="discountedPrice"
          :key="item.name"
        />
      </div>
    </section>
    
    <Contact />

    <footer class="footer mt-3 p-5 text-lg">
      <p>{{ copyright }}</p>
    </footer>
  </div>
</template>

<script>
import MenuItem from "@/components/MenuItem";
import Header from "@/components/Header";
import Contact from "@/components/Contact";

export default {
  // el: "#app",
  components: {
    MenuItem,
    Header,
    Contact,
  },
  data: function() {
    return {
      address: "9274 Beurre Ave, Paris, France",
      email: "hello@cafewithavue.bakery",
      phone: "+08 88 88 88 88 88",
      restaurantName: "Cafe with A Vue",
      restaurantNameHeader:
        "<span class='text-white'> Cafe </span> with <span class='text-h1'> A </span> Vue",
      shoppingCart: 0,
      backgroundImage: {
        headerImage: "images/header-image-restaurant-food-wraps.png",
        altHeaderImage: "header_image_restaurant_food_wraps",
      },
      simpleMenu: [
        {
          name: "Crossiant",
          image: {
            source: "images/crossiant.jpg",
            alt: "A crossiant",
          },
          inStock: true,
          quantity: 1,
          price: 2.99,
        },
        {
          name: "French Baguette",
          image: {
            source: "images/french-baguette.jpeg",
            alt: "Four French Baguettes",
          },
          inStock: true,
          quantity: 1,
          price: 3.99,
        },
        {
          name: "Éclair",
          image: {
            source: "images/eclair.jpg",
            alt: "Chocolate Éclair",
          },
          inStock: false,
          quantity: 1,
          price: 4.99,
        },
      ],
    };
  },
  computed: {
    copyright() {
      const currentYear = new Date().getFullYear();
      return `Copyright ${this.restaurantName} ${currentYear}`;
    },
  },
  methods: {
    addToShoppingCart(amount) {
      this.shoppingCart += amount;
    },
  },
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=DM+Serif+Display:ital@0;1&display=swap");
#app {
  font-family: "DM Serif Display", serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

ul > li {
  list-style: none;
}
.imagetextcenter {
  position: absolute;
  top: 60%;
  left: 50%;
  transform: translate(-50%, -50%);
}
@media only screen and (max-width: 768px) {
  .imagetextcenter {
    position: absolute;
    top: 25% !important;
    left: 50%;
    transform: translate(-50%, -50%);
  }
  .shopping-cart {
    position: absolute;
    right: 0px;
    top: 0;
  }
}

.description {
  max-width: 960px;
  font-size: 1.2rem;
  margin: 0 auto;
}

.footer {
  text-align: center;
  font-style: italic;
}

.menu {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}

.shopping-cart {
  position: absolute;
  right: 30px;
  top: 0;
}
</style>
