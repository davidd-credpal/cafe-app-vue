<script>
export default {
  name: 'Contact',
  data() {
    return {
      address: '9274 Beurre Ave, Paris, France',
      email: 'hello@cafewithavue.bakery',
      phone: '+08 88 88 88 88 88'
    }
  }
}
</script>

<template>
  <div>
   <div>
      <h2 class="text-3xl mt-8 text-h1 uppercase">Contact Us</h2>
      <p class=" tracking-wider">Address: {{ address }}</p>
      <p class=" tracking-wider">Phone: {{ phone }}</p>
      <p class=" tracking-wider">Email: {{ email }}</p>
      <p class="text-2xl m-3 text-h1 uppercase">Hours:</p>
      <ul>
        <li>Monday-Friday: 06:00 to 16:00</li>
        <li>Saturday: 07:00 to 14:00</li>
        <li>Sunday: 07:00 to 12:00</li>
      </ul>
    </div>
  </div>
</template>

<style></style>
