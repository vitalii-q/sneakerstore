<template>
  <div class="fixed top-0 left-0 h-full w-full bg-black z-10 opacity-70"></div>
  <div class="bg-white w-96 h-full fixed right-0 top-0 z-20 p-8">
    <DrawerHead />

    <CartItemList />

    <div class="flex flex-col gap-4 my-7">
      <div class="flex gap-2">
        <span>Total:</span>
        <div class="flex-1 border-b border-dashed"></div>
        <b>99 €</b>
      </div>

      <div class="flex gap-2">
        <span>Tax 5%:</span>
        <div class="flex-1 border-b border-dashed"></div>
        <b>9 €</b>
      </div>

      <button disabled=""
              class="mt-4 transition bg-line-500 w-full rounded-xl py-3 text-white disabled:bg-slate-300 hover:bg-lime-600 active:bg-lime-700 cursor-pointer">
        Order
      </button>
    </div>
  </div>
</template>

<script>
// eslint-disable-next-line no-unused-vars
import DrawerHead from "@/components/DrawerHead.vue";
import CartItemList from "@/components/CartItemList.vue";

export default {
  // eslint-disable-next-line vue/multi-word-component-names
  name: "Drawer",
  components: {CartItemList, DrawerHead}
}
</script>

<style scoped>

</style>
