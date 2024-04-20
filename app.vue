<template>
  <div class="container pt-4 mx-auto">
      <div class="flex flex-row justify-between">
        <TodoViewer title="Nuxt 3 fundamentals">
          <template v-slot:hero>
            <img src="~/public/todolist.jpg" class="w-1/3"/>
            <p>
              Photo by <a href="https://unsplash.com/@glenncarstenspeters?utm_content=creditCopyText&utm_medium=referral&utm_source=unsplash">Glenn Carstens-Peters</a> on <a href="https://unsplash.com/photos/person-writing-bucket-list-on-book-RLw-UC03Gwc?utm_content=creditCopyText&utm_medium=referral&utm_source=unsplash">Unsplash</a>
            </p>
          </template>
          <template v-slot:metrics="slotProps">
            <span class="block">Number of todos {{slotProps.numbersOfTodos}}</span>
            <span class="block">Finished todos {{slotProps.finishedTodos}}</span> 
          </template>
          
        </TodoViewer>
        <PhotoGallery />
      </div>
  </div>
</template>
<script setup>
import TodoViewer from "~/components/TodoViewer.vue";
import PhotoGallery from "~/components/PhotoGallery.vue";


</script>