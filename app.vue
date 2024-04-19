<template>
  <div class="container m-auto">
    <div class="flex flex-col">
      <h1 class="text">Photo Gallery</h1>
      <button class="bg-emerald-600" @click="fetchPhotoGallery" >Fetch Photos</button>
      <div class="grid grid-cols-3 gap-4">
        <div v-for="photo in photoGallery" :key="`photo-id-${photo.id}`" class="border">
          <img :src="photo.url" alt="photo.title" class="w-full h-40 object-cover" />
          <p>{{ photo.title }}</p>
        </div>
      </div>
    </div>
    <pre>
      {{ photoGallery }}
    </pre>
  </div>
  <NuxtPage />
</template>


<script>
import {defineNuxtComponent} from "#app";

export default defineNuxtComponent({
  data() {
    return {
      photoGallery: [],
    }
  },
  methods: {
    async fetchPhotoGallery() {
      const response = await fetch('https://jsonplaceholder.typicode.com/photos')
      this.photoGallery = await response.json()
    }
  }
})

</script>