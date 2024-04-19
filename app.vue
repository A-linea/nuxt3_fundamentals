<template>
  <div class="container m-auto">
    <div class="flex flex-col">
      <h1 class="text">Photo Gallery</h1>
      <button class="bg-emerald-600 p-3 mt-3" @click="fetchPhotoGallery" >Fetch Photos</button>
      <p v-if="numPhotos > 0" class="mt-3">Number of photos: {{ numPhotos }}</p>
      <p>Even photos is  {{evenPhotos.length}} ||| Odd photos is {{oddPhotos.length}}</p>
      <div class="grid grid-cols-3 gap-4">
        <div v-for="photo in photoGallery" :key="`photo-id-${photo.id}`" class="border">
          <img :src="photo.url" :alt="photo.title" class="w-full h-40 object-cover" />
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
  
  computed: {
    numPhotos() {
      return this.photoGallery.length
    },
    evenPhotos() {
      return this.photoGallery.filter((photo, index) => index % 2 === 0)
    },
    oddPhotos() {
      return this.photoGallery.filter((photo, index) => index % 2 !== 0)
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