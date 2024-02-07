<script setup>
import Card from "./Card.vue";

defineProps({
  items: Array
})

const onClickAdd = () => {
  alert('D');
}
</script>

<template>
  <div class="grid grid-cols-4 gap-5">
    <Card
      v-for="item in items"
      :key="item.id"
      :title="item.title"
      :imageUrl="item.imageUrl"
      :price="item.price"
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
