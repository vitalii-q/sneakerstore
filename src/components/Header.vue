<script setup>
const emit = defineEmits(['openDrawer']);

defineProps({ // вытаскиваем значения
  totalPrice: Number
})
</script>

<template>
  <header class="flex justify-between border-b border-slate-200 px-8 py-8">

    <router-link to="/">
      <div class="flex items-center gap-4">
        <img src="/logo.png" alt="logo" class="w-10" />
        <div>
          <h2 class="text-xl font-bold uppercase">Sneaker store</h2>
          <p class="text-slate-400">Store for the best sneakers</p>
        </div>
      </div>
    </router-link>

    <ul class="flex items-center gap-10">
      <li @click="() => emit('openDrawer')" class="flex items-center cursor-pointer gap-3 text-gray-500 hover:text-black">
        <img src="/cart.svg" alt="cart" />
        <b>{{ totalPrice }} €</b>
      </li>

      <router-link to="/favorites">
        <li class="flex items-center cursor-pointer gap-3 text-gray-500 hover:text-black">
          <img src="/heart.svg" alt="heart" />
          <b>Bookmarks</b>
        </li>
      </router-link>

      <li class="flex items-center cursor-pointer gap-3 text-gray-500 hover:text-black">
        <img src="/profile.svg" alt="profile" />
        <b>Profile</b>
      </li>
    </ul>

  </header>
</template>

<script>
export default {
  name: "Header"
}
</script>

<style scoped>

</style>
