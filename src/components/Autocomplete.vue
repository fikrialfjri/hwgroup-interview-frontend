<template>
  <div class="space-y-6">
    <div class="w-1/2 mx-auto">
      <input
        v-model="search"
        type="text"
        class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-neutral-800 focus:border-neutral-800 block w-full p-2.5"
        placeholder="Type to search"
      />
    </div>
    <div v-show="searchResults.length">
      <PhotoGallery :data="searchResults" />
    </div>
  </div>
</template>

<script setup>
import { computed, ref } from "vue";
import PhotoGallery from "./PhotoGallery.vue";

const { data } = defineProps(["data"]);

const search = ref("");

const searchResults = computed(() => {
  if (!search.value.length) return [];

  return data.filter((item) => item.title.toLowerCase().includes(search.value.toLowerCase()));
});
</script>
