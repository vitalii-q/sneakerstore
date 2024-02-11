<script setup>
import { ref, onMounted } from "vue";
import axios from "axios";
import CardList from "@/components/CardList.vue";

const favorites = ref([])

onMounted(async () => {
  try {
    const { data } = await axios.get('https://e974a97937eaa83d.mokky.dev/favorites?_relations=items')

    favorites.value = data.map(obj => obj.item)
  } catch (err) {
    console.log(err)
  }
})
</script>

<template>
  <h1 class="text-3xl font-bold mb-8">My bookmarks</h1>

  <CardList :items="favorites" is-favorites />
</template>

<script>
export default {
  name: "Favorites"
}
</script>

<style scoped>

</style>
