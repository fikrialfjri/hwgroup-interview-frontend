<template>
  <div class="grid grid-cols-2 gap-3 md:grid-cols-3 lg:grid-cols-4">
    <div v-for="(item, index) in data" :key="index">
      <Image :src="item.image_url" :alt="item.title" :rating="item.rating" />
    </div>
  </div>
</template>

<script setup>
import Image from "./Image.vue";

defineProps(["data"]);
</script>
