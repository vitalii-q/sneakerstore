<script setup>
import DrawerHead from "@/components/DrawerHead.vue";
import CartItemList from "@/components/CartItemList.vue";
import InfoBlock from "@/components/InfoBlock.vue";

const emit = defineEmits(['createOrder'])

defineProps({
  totalPrice: Number,
  vatPrice: Number,
  buttonDisabled: Boolean,
})
</script>

<template>
  <div class="fixed top-0 left-0 h-full w-full bg-black z-10 opacity-70"></div>
  <div class="bg-white w-96 h-full fixed right-0 top-0 z-20 p-8">
    <DrawerHead />

    <div v-if="!totalPrice" class="flex h-full items-center">
      <InfoBlock
        title="Cart is empty"
        description="Add at least one pair of sneakers to place an order."
        image-url="/package-icon.png"
      />
    </div>

    <div v-else>
      <CartItemList />

      <div class="flex flex-col gap-4 my-7">
        <div class="flex gap-2">
          <span>Total:</span>
          <div class="flex-1 border-b border-dashed"></div>
          <b>{{ totalPrice }} €</b>
        </div>

        <div class="flex gap-2">
          <span>Tax 5%:</span>
          <div class="flex-1 border-b border-dashed"></div>
          <b>{{ vatPrice }} €</b>
        </div>

        <button
          :disabled="buttonDisabled"
          @click="() => emit('createOrder')"
          class="mt-4 transition bg-lime-500 w-full rounded-xl py-3 text-white disabled:bg-slate-300 hover:bg-lime-600 active:bg-lime-700 cursor-pointer">
          Order
        </button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Drawer",
}
</script>

<style scoped>

</style>
