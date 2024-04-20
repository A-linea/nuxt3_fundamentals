<template>
    <div class="flex flex-col w-1/2">
     
      <h1 class="columns-1 text-2xl text-blue-700"> {{title}} </h1>
      <button @click="fetchTodoList" class="mt-2 w-1/6 bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded">Fetch Todo List</button>
      <div class="mt-3">
        <slot name="hero"></slot>
        <slot name="metrics" :="{numbersOfTodos, finishedTodos}"></slot>
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
</template>
<script setup>

import {ref, computed, defineProps} from "vue";

defineProps({
  title: {
    type: String,
    default: 'Todo Viewer'
  },
})


const todoList = ref([]);
const numbersOfTodos = computed(() => todoList.value.length)
const finishedTodos = computed(() => todoList.value.filter(todo => todo.completed).length)
async function fetchTodoList() {
  const resp  = await fetch('https://jsonplaceholder.typicode.com/todos')
  todoList.value = await resp.json()
  }

</script>