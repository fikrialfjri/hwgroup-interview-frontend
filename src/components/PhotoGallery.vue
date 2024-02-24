<template>
  <div class="grid grid-cols-2 md:grid-cols-3 lg:grid-cols-4 gap-3">
    <div v-for="(item, index) in data" :key="index">
      <img class="w-full h-full object-cover rounded-lg" :src="item.image_url" :alt="item.title" />
    </div>
  </div>
</template>

<script setup>
defineProps({
  data: Array,
});
</script>
