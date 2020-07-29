<template>
  <div id="app" class="lg:container lg:mx-auto h-full bg-green-100 w-full">
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
      <h2 class="text-4xl text-center uppercase font-semibold text-h1 text-o">
        Menu
      </h2>
      <menuItem :addToShoppingCartFunc="addToShoppingCart" />
    </section>
    <div>
      <h2 class="text-3xl mt-8 text-h1 uppercase">Contact Us</h2>
      <p>Address: {{ address }}</p>
      <p>Phone: {{ phone }}</p>
      <p>Email: {{ email }}</p>
      <p class="text-2xl m-3 text-h1 uppercase">Hours:</p>
      <ul>
        <li>Monday-Friday: 06:00 to 16:00</li>
        <li>Saturday: 07:00 to 14:00</li>
        <li>Sunday: 07:00 to 12:00</li>
      </ul>
    </div>

    <footer class="footer mt-3 p-5 text-lg">
      <p>{{ copyright }}</p>
    </footer>
  </div>
</template>

<script>
import MenuItem from "@/components/MenuItem";
import Header from "@/components/Header";

export default {
  el: "#app",
  components: {
    MenuItem,
    Header,
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
/* .background-image {
  background-color: linear-gradient(rgba(0, 0, 0, 0.5), rgba(175, 56, 56, 0.5));
} */
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
