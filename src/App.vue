<script setup>
import Header from "@/components/Header.vue";
import CardList from "@/components/CardList.vue";
import Drawer from "@/components/Drawer.vue";
</script>

<template>
  <Drawer />

  <div class="bg-white w-4/5 m-auto h-screen rounded-xl shadow-xl mt-14">
    <Header />

    <div class="p-10">
      <div class="flex justify-between">
        <h2 class="text-3x1 font-bold mb-8">All sneakers</h2>
      </div>

      <CardList />
    </div>
  </div>
</template>
