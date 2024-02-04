<template>
  <header class="flex justify-between border-b border-slate-200 px-8 py-8">

    <div class="flex items-center gap-4">
      <img src="/logo.png" alt="logo" class="w-10" />
      <div>
        <h2 class="text-xl font-bold uppercase">Sneaker store</h2>
        <p class="text-slate-400">Store for the best sneakers</p>
      </div>
    </div>

    <ul class="flex items-center gap-10">
      <li class="flex items-center cursor-pointer gap-3 text-gray-500 hover:text-black">
        <img src="/cart.svg" alt="cart" />
        <b>205 €</b>
      </li>

      <li class="flex items-center cursor-pointer gap-3 text-gray-500 hover:text-black">
        <img src="/heart.svg" alt="heart" />
        <b>Bookmarks</b>
      </li>

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
