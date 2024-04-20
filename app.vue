<template>
  <div class="container pt-4 mx-auto">
      <div class="flex flex-row justify-between">
        <TodoViewer title="Todo List">
        </TodoViewer>
        <PhotoGallery title="Photo Gallery List" />
      </div>
  </div>
</template>
<script setup>
import TodoViewer from "~/components/TodoViewer.vue";
import PhotoGallery from "~/components/PhotoGallery.vue";


</script>