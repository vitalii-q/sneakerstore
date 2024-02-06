<template>
  <div class="flex items-center border border-stale-100 p-4 rounded-xl gap-4">
    <img class="w-16 h-16" src="/sneakers/sneakers-1.jpg" alt="" />

    <div class="flex flex-col">
      <p>Кроссовки Nike Air Max 70</p>

      <div class="flex justify-between mt-2">
        <b>129 €</b>
        <img class="opacity-40 hover:opacity-100 cursor-pointer transition" src="/close.svg"  alt=""/>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "CartItem"
}
</script>

<style scoped>

</style>
