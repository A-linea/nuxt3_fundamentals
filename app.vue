<template>
  <div class="container m-auto">
    <div class="flex flex-col">
      <h1 class="columns-1 text-2xl text-blue-700">Nuxt 3 fundamentals</h1>
      <button @click="fetchTodoList" class="mt-2 w-1/6 bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded">Fetch Todo List</button>
    </div>
    <div class="flex">
      <div class="mt-3">
        <img src="/todolist.jpg" class="w-1/3"/>
        <p>
          Photo by <a href="https://unsplash.com/@glenncarstenspeters?utm_content=creditCopyText&utm_medium=referral&utm_source=unsplash">Glenn Carstens-Peters</a> on <a href="https://unsplash.com/photos/person-writing-bucket-list-on-book-RLw-UC03Gwc?utm_content=creditCopyText&utm_medium=referral&utm_source=unsplash">Unsplash</a>
        </p>
        <template v-if="todoList">
          <ul>
            <li v-for="todo in todoList" :key="todo.id">
              <strong class="w-[30px] inline-block">{{todo.id}}</strong>
              <input class="mr-2" type="checkbox" :checked="todo.completed"/>
              {{ todo.title }}</li>
          </ul>
        </template>
      </div>
  </div>
  </div>
</template>
<script>
import {defineNuxtComponent} from "#app";

export default defineNuxtComponent({
  data() {
    return {
      todoList: [],
    }
  },
  methods: {
    async fetchTodoList() {
      const response = await fetch('https://jsonplaceholder.typicode.com/todos')
      this.todoList = await response.json()
    }
  }
})

</script>