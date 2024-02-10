<script setup>
const { cart, removeFromCart } = inject('cart')
</script>

<template>
  <div class="flex flex-col gap-5" v-auto-animate>
    <CartItem
      v-for="item in cart"
      :key="item.id"
      :title="item.title"
      :price="item.price"
      :image-url="item.imageUrl"
      @on-click-remove="() => removeFromCart(item)"
    />
  </div>
</template>

<script>
// eslint-disable-next-line no-unused-vars
import CartItem from "@/components/CartItem.vue";
import {inject} from "vue";

export default {
  name: "CartItemList",
  components: {CartItem}
}
</script>

<style scoped>

</style>
