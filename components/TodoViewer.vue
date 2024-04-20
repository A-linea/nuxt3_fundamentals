<template>
<!--   we passed itemList from GenericComponent where we listening for the update:itemList event-->
  <GenericComponent :title="title" itemType="todos" v-model:item-list="todoList">
    <template v-slot:hero>
      <img src="~/public/todolist.jpg" class="w-1/3"/>
      <p>
        Photo by <a href="https://unsplash.com/@glenncarstenspeters?utm_content=creditCopyText&utm_medium=referral&utm_source=unsplash">Glenn Carstens-Peters</a> on <a href="https://unsplash.com/photos/person-writing-bucket-list-on-book-RLw-UC03Gwc?utm_content=creditCopyText&utm_medium=referral&utm_source=unsplash">Unsplash</a>
      </p>
    </template>
    <template v-slot:metrics>
      <span class="block">Number of todos {{numbersOfTodos}}</span>
      <span class="block">Finished todos {{finishedTodos}}</span>
    </template>
    <template v-slot:items>
      <li v-for="item in todoList">
        <input class="inline-block mr-[30px]" type="checkbox" :checked="item.completed">
        <span>{{item.title}}</span>
      </li>
    </template>
  </GenericComponent>
   
</template>
<script setup>

import {ref, computed, defineProps} from "vue";
import GenericComponent from "~/components/GenericComponent.vue";
defineProps({
  title: {
    type: String,
    default: 'Todo Viewer'
  },
})


const todoList = ref([]);
const numbersOfTodos = computed(() => todoList.value.length)
const finishedTodos = computed(() => todoList.value.filter(todo => todo.completed).length)

</script>