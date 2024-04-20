<template>

  <div class="flex flex-col w-1/2">
    <h1 class="text">Photo Gallery</h1>
    <button class="bg-emerald-600 p-3 mt-3 text-white" @click="fetchPhotoGallery">Fetch Photos</button>
    <p v-if="numPhotos > 0" class="mt-3">Number of photos: {{ numPhotos }}</p>
    <p>Even photos is {{ evenPhotos.length }} ||| Odd photos is {{ oddPhotos.length }}</p>
    <div class="grid grid-cols-3 gap-4">
      <div v-for="photo in photoGallery" :key="`photo-id-${photo.id}`" class="border">
        <img :src="photo.url" :alt="photo.title" class="w-full h-40 object-cover"/>
        <p>{{ photo.title }}</p>
      </div>
    </div>
  </div>
</template>


<script setup>
import {ref, computed} from 'vue'

let photoGallery = ref([]) 
    
const numPhotos = computed(() => photoGallery.value.length)
const evenPhotos = computed(() => photoGallery.value.filter((photo, index) => index % 2 === 0))
const oddPhotos = computed(() => photoGallery.value.filter((photo, index) => index % 2 !== 0))
async function fetchPhotoGallery() {
  const response = await fetch('https://jsonplaceholder.typicode.com/photos')
  photoGallery.value = await response.json()

}
</script>