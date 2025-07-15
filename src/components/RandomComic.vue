<template>
  <div class="text-center">
    <div v-if="comic">
      <img :src="comic.img" :alt="comic.alt" class="img-fluid" />
    </div>
    <button class="btn btn-primary mt-3" @click="fetchComic">Load Another Comic</button>
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue'

const comic = ref(null)

const fetchComic = async () => {
  const randomNum = Math.floor(Math.random() * 2800) + 1
  const url = `https://xkcd.com/${randomNum}/info.0.json`
  const proxyUrl = `https://api.allorigins.win/raw?url=${url}`

  try {
    const res = await fetch(proxyUrl)
    comic.value = await res.json()
  } catch (error) {
    console.error('Failed to fetch comic:', error)
  }
}

onMounted(fetchComic)
</script>
