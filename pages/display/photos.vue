<script setup>

import PhotoGallery from "~/components/PhotoGallery.vue";
import TodoViewer from "~/components/TodoViewer.vue";
</script>

<template>
  <Title>Photos</Title>
  <div class="container pt-4 mx-auto">
    <div class="flex flex-row justify-between">
      <PhotoGallery title="Photo Gallery List" />
    </div>
  </div>
</template>

<style scoped>

</style>