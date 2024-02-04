<template>
  <div class="grid grid-cols-4 gap-5">
    <Card />
    <Card />
    <Card />
    <Card />
    <Card />
    <Card />
  </div>
</template>

<script>
import Card from "@/components/Card.vue";

export default {
  name: "CardList",
  components: {Card}
}
</script>

<style scoped>

</style>
