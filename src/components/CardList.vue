<script setup>
import Card from "./Card.vue";

const onClickAdd = () => {
  alert('D');
}
</script>

<template>
  <div class="grid grid-cols-4 gap-5">
    <Card
      title="Nike Blazer Mid Suede"
      imageUrl="/sneakers/sneakers-1.jpg"
      :price="170"
      :is-added="true"
      :is-favorite="false"
      :onClickAdd="onClickAdd"
    />
  </div>
</template>

<script>
export default {
  name: "CardList",
}
</script>

<style scoped>

</style>
