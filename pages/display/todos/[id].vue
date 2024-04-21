
<script setup>

const route = useRoute();
definePageMeta({
  layout: 'custom'
});

</script>

<template>
  <div>
     {{route.path}}
  </div>
</template>

<style scoped>

</style>