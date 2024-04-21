<script setup >
import TodoViewer from "~/components/TodoViewer.vue";
</script>

<template>
  <Title>Todos</Title>
  <div class="container pt-4 mx-auto">
    <div class="flex flex-row justify-between">
      <TodoViewer title="Todo List">
      </TodoViewer>
    </div>
  </div>
</template>

<style scoped>

</style>