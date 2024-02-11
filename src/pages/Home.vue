<script setup>
import {onMounted, reactive, ref, watch} from "vue";
import axios from "axios";
import { inject } from "vue";
import CardList from "@/components/CardList.vue";

const { cart, addToCart, removeFromCart } = inject('cart')

const items = ref([]) // для массивов применяют ref

const filters = reactive({ // для обычных объектов применяют reactive
  sortBy: 'title',
  searchQuery: '',
})

const onClickAddPlus = (item) => {
  if(!item.isAdded) {
    addToCart(item)
  } else {
    removeFromCart(item)
  }

  console.log(cart);
}

const onChangeSelect = (event) => {
  filters.sortBy = event.target.value;
}

const onChangeSearchInput = (event) => {
  filters.searchQuery = event.target.value;
}

const fetchFavorites = async () => {
  try {
    const { data:favorites } = await axios.get('https://e974a97937eaa83d.mokky.dev/favorites')
    items.value = items.value.map(item => {
      const favorite = favorites.find((favorite) => favorite.product_id === item.id);

      if (!favorite) {
        return item;
      }

      return {
        ...item,
        isFavorite: true,
        favoriteId: favorite.id,
      }
    })
  } catch (err) {
    console.log(err)
  }
}

const fetchItems = async () => {
  try {
    const params = {
      sortBy: filters.sortBy
    }

    if (filters.searchQuery) {
      params.title = `*${filters.searchQuery}*`
    }

    const { data } = await axios.get('https://e974a97937eaa83d.mokky.dev/items', {params})
    items.value = data.map((obj) => ({
      ...obj,
      isFavorite: false,
      favoriteId: null,
      isAdded: false
    }))
  } catch (err) {
    console.log(err)
  }
}

const addToFavorite = async (item) => {
  try {
    if(!item.isFavorite) {
      const obj = {
        product_id: item.id
      };

      item.isFavorite = true

      const { data } = await axios.post('https://e974a97937eaa83d.mokky.dev/favorites', obj)

      item.favoriteId = data.id // сохраняем во фронте
    } else {
      item.isFavorite = false
      await axios.delete(`https://e974a97937eaa83d.mokky.dev/favorites/${item.favoriteId}`)
      item.favoriteId = null
    }
  } catch (err) {
    console.log(err)
  }
}

onMounted(async () => {
  const localCart = localStorage.getItem('cart')
  cart.value = localCart ? JSON.parse(localCart) : []

  await fetchItems()
  await fetchFavorites()

  items.value = items.value.map((item) => ({
    ...item,
    isAdded: cart.value.some((cartItem) => cartItem.id === item.id)
  }))
})

watch(cart, () => {
  items.value = items.value.map((item) => ({
    ...item,
    isAdded: false
  }))
})

watch(filters, fetchItems)
</script>

<template>
  <div class="flex justify-between items-center">
    <h2 class="text-3x1 font-bold mb-8">All sneakers</h2>

    <div class="flex gap-4">
      <select @change="onChangeSelect" class="py-2 px-3 border rounded-md outline-none">
        <option value="name">By name</option>
        <option value="price">By price (Cheap)</option>
        <option value="-price">By price (Expensive)</option>
      </select>

      <div class="relative">
        <img class="absolute left-4 top-3" src="/search.svg" alt="search">
        <input class="border rounded-md py-2 pl-11 pr-4 outline-none focus:border-gray-400"
               type="text"
               placeholder="Search..."
               @input="onChangeSearchInput"
        />
      </div>
    </div>
  </div>

  <div class="mt-10">
    <CardList :items="items" @addToFavorite="addToFavorite" @add-to-cart="onClickAddPlus" />
  </div>
</template>

<script>
export default {
  name: "Home",
}
</script>

<style scoped>

</style>
