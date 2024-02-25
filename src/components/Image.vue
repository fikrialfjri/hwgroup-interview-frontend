<template>
  <div :class="{ 'w-full p-2 border border-neutral-100 shadow-custom bg-white rounded-lg': variant === 'composition' }" class="relative">
    <Tooltip :tooltip="tooltip">
      <img :src="src" :alt="alt" :class="classes" class="object-cover w-full h-full rounded-lg" />
    </Tooltip>
    <h1 v-show="variant === 'composition'" class="ml-1">{{ title }}</h1>
    <div
      :class="{
        'w-28 right-0 mx-auto top-auto bottom-5 rounded-lg': ratingPosition === 'center',
        'relative top-0 left-0 bg-transparent w-fit justify-start pl-1': variant === 'composition',
      }"
      class="absolute flex items-center justify-center py-1.5 left-0 bg-neutral-800 shadow-2xl pl-3 pr-4 top-5 rounded-r-lg"
    >
      <StarRating :rating="rating" class="" />
    </div>
  </div>
</template>

<script setup>
import StarRating from "./StarRating.vue";
import Tooltip from "./Tooltip.vue";

defineProps(["src", "alt", "classes", "rating", "ratingPosition", "tooltip", "variant", "title"]);
</script>
