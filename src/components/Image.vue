<template>
  <Tooltip :tooltip="tooltip">
    <img :src="src" :alt="alt" :class="classes" class="object-cover w-full h-full rounded-lg" />
    <div
      :class="ratingPosition === 'center' ? 'w-28 right-0 mx-auto bottom-5 rounded-lg' : 'pl-3 pr-4 top-5 rounded-r-lg'"
      class="absolute flex items-center justify-center py-1.5 left-0 bg-neutral-800 shadow-2xl"
    >
      <StarRating :rating="rating" class="" />
    </div>
  </Tooltip>
</template>

<script setup>
import StarRating from "./StarRating.vue";
import Tooltip from "./Tooltip.vue";

defineProps(["src", "alt", "classes", "rating", "ratingPosition", "tooltip"]);
</script>
