<script setup>
import DrawerHead from "@/components/DrawerHead.vue";
import CartItemList from "@/components/CartItemList.vue";
import InfoBlock from "@/components/InfoBlock.vue";
import axios from "axios";
import {computed, inject, ref} from "vue";

const props = defineProps({
  totalPrice: Number,
  vatPrice: Number,
})

const { cart, closeDrawer } = inject('cart')

const isCreating = ref(false)
const orderId = ref(null)

const createOrder = async () => {
  isCreating.value = true

  try {
    const { data } = await axios.post('https://e974a97937eaa83d.mokky.dev/orders', {
      items: cart,
      totalPrice: props.totalPrice.value
    })

    cart.value = []

    orderId.value = data.id
  } catch (err) {
    console.log(err)
  } finally {
    isCreating.value = false
  }
}

const cartIsEmpty = computed(() => cart.value.length === 0 )
const buttonDisabled = computed(() => isCreating.value || cartIsEmpty.value)
</script>

<template>
  <div class="fixed top-0 left-0 h-full w-full bg-black z-10 opacity-70"></div>
  <div class="bg-white w-96 h-full fixed right-0 top-0 z-20 p-8">
    <DrawerHead />

    <div v-if="!totalPrice" class="flex h-full items-center">
      <InfoBlock
        v-if="!totalPrice && !orderId"
        title="Cart is empty"
        description="Add at least one pair of sneakers to place an order."
        image-url="/package-icon.png"
      />

      <InfoBlock
        v-if="orderId"
        title="Order placed!"
        :description="`Your order #${orderId} will soon be handed over to shipping`"
        image-url="/order-success-icon.png"
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
          @click="createOrder"
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
