<template>
  <div class="relative overflow-hidden max-w-[60vw] mx-auto rounded-2xl">
    <div class="flex transition-transform duration-500 ease-out" :style="{ transform: `translateX(-${currImage * 100}%)` }">
      <img v-for="(item, index) in data" :key="index" :src="item.image_url" :alt="item.title" class="min-w-[60vw] max-w-[60vw]" />
    </div>

    <div className="absolute inset-0 flex items-center justify-between p-4">
      <button class="flex items-center justify-center w-8 h-8 bg-white border rounded-full shadow-xl border-neutral-100" @click="prev">◀</button>
      <button class="flex items-center justify-center w-8 h-8 bg-white border rounded-full shadow-xl border-neutral-100" @click="next">▶</button>
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from "vue";

const { data } = defineProps(["data"]);

const currImage = ref(0);
const prev = () => (currImage.value = currImage.value === 0 ? data.length - 1 : currImage.value - 1);
const next = () => (currImage.value = currImage.value === data.length - 1 ? 0 : currImage.value + 1);

const autoSlideInterval = 2000;
let autoSlideTimer;

const startAutoSlide = () => (autoSlideTimer = setInterval(() => next(), autoSlideInterval));
const stopAutoSlide = () => clearInterval(autoSlideTimer);

onMounted(startAutoSlide);
onUnmounted(stopAutoSlide);
</script>
