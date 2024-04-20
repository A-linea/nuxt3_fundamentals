<script setup>
import {ref, defineProps, defineEmits} from "vue";

const props = defineProps({
  itemList: {
    type: Array,
    default: () => []
  },
  title: {
    type: String,
    required: true
  },
  itemType: {
    type: String,
    default: 'todos'
  }
})
const emit = defineEmits(['update:itemList'])
const itemList = ref([]);

async function fetchItemList() {
  const response = await fetch(`https://jsonplaceholder.typicode.com/${props.itemType}`)
  const data = await response.json()
  emit('update:itemList', data)
}
</script>

<template>
  <div class="flex flex-col w-1/2">
    <h1 class="mb-4 text-xl">{{ title }}</h1>
    <slot name="hero"></slot>
    <slot name="metrics"></slot>
    <button class="button bg-emerald-600 p-3 mt-3 text-white w-1/6 rounded mb-3" @click="fetchItemList">Fetch Data</button>
    <ul class="pl-3">
      <slot name="items"></slot>
    </ul>
  </div>
</template>

<style scoped>

</style>