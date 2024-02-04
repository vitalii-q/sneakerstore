<template>
    <div class="relative bg-white border border-stale-100 rounded-3xl p-8 cursor-pointer transition hover:-translate-y-2 hover:shadow-xl">
      <img src="/like-1.svg" alt="like 1" class="absolute top-8 left-8">
      <img src="/sneakers/sneakers-1.jpg" alt="sneaker">
      <p>Nike Blazer Mid Suede</p>

      <div class="flex justify-between mt-5">
        <div class="flex flex-col">
          <span class="text-slate-400">Цена:</span>
          <b>205 €</b>
        </div>

        <img src="/plus.svg" alt="Plus" />
      </div>
    </div>
</template>

<script>
export default {
  name: "Card"
}
</script>

<style scoped>

</style>
