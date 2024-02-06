<template>
  <div class="flex flex-col gap-5">
    <CartItem />
    <CartItem />
    <CartItem />
  </div>
</template>

<script>
// eslint-disable-next-line no-unused-vars
import CartItem from "@/components/CartItem.vue";

export default {
  name: "CartItemList",
  components: {CartItem}
}
</script>

<style scoped>

</style>
