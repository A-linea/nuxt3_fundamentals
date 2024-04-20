<template>
  <GenericComponent :title="title" itemType="photos" v-model:item-list="photoGallery">

    <template v-slot:items>
      <div class="grid grid-cols-3 gap-4">
        <li v-for="photo in photoGallery" :key="`photo-id-${photo.id}`" class="border">
          <img :src="photo.url" :alt="photo.title" class="w-full h-40 object-cover"/>
          <p>{{ photo.title }}</p>
        </li>
      </div>
    </template>

  </GenericComponent>

</template>


<script setup>
import {ref, computed, defineProps} from 'vue'
import GenericComponent from "~/components/GenericComponent.vue";

defineProps({
  title: {
    type: String,
    default: 'Photo Gallery'
  },
  itemType: {
    type: String,
    default: 'photos'
  }
})

let photoGallery = ref([])

const numPhotos = computed(() => photoGallery.value.length)
const evenPhotos = computed(() => photoGallery.value.filter((photo, index) => index % 2 === 0))
const oddPhotos = computed(() => photoGallery.value.filter((photo, index) => index % 2 !== 0))

</script>
<!--here we can rewrite the style of button in the GenericComponent to use the ::v-deep selector-->
<style scoped>

::v-deep(.button) {
  background-color: #0249f6 !important;
  color: white;
  padding: 14px 20px;
  margin: 8px 0;
  border: none;
  cursor: pointer;
  width: 30%;
}
</style>