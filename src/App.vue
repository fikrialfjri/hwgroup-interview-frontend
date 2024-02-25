<template>
  <div class="w-screen px-5 py-6 space-y-3">
    <ul class="flex flex-wrap text-sm font-medium text-center text-gray-500 dark:text-gray-400">
      <li
        v-for="(item, index) in viewDataTabs"
        :key="index"
        @click="viewData = item"
        class="inline-block px-4 py-3 border rounded-lg cursor-pointer me-2 border-neutral-500"
        :class="viewData === item ? 'bg-neutral-900 text-yellow-300' : 'bg-gray-100 hover:bg-gray-200 hover:text-gray-900'"
      >
        {{ item }}
      </li>
    </ul>

    <PhotoGallery v-if="viewData === 'Gallery View'" :data="images" />
    <ImageCarousel v-else :data="images" />
  </div>
</template>

<script setup>
import { ref } from "vue";
import images from "@/assets/json/images.json";
import PhotoGallery from "@/components/PhotoGallery.vue";
import ImageCarousel from "@/components/ImageCarousel.vue";

const viewDataTabs = ["Gallery View", "Carousel View"];
const viewData = ref(viewDataTabs[0]);
</script>
