<template>
  <div class="w-screen py-6 px-5 space-y-3">
    <PhotoGallery :data="images" />
  </div>
</template>

<script setup>
import images from "@/assets/json/images.json";
import PhotoGallery from "@/components/PhotoGallery.vue";
</script>
