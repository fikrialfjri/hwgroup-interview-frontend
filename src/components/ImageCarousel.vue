<template>
  <div class="relative overflow-hidden max-w-[calc(100vw-40px)] mx-auto rounded-2xl">
    <div class="flex transition-transform duration-500 ease-out" :style="{ transform: `translateX(-${currImage * 100}%)` }">
      <Image
        v-for="(item, index) in data"
        :key="index"
        :src="item.image_url"
        :alt="item.title"
        :rating="item.rating"
        ratingPosition="center"
        classes="min-w-[calc(100vw-40px)] max-w-[calc(100vw-40px)] h-[calc(100vh-110px)]"
      />
    </div>

    <div className="absolute inset-0 flex items-center justify-between p-4">
      <button class="flex items-center justify-center w-8 h-8 text-yellow-300 rounded-full shadow-2xl bg-neutral-800" @click="prev">◀</button>
      <button class="flex items-center justify-center w-8 h-8 text-yellow-300 rounded-full shadow-2xl bg-neutral-800" @click="next">▶</button>
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from "vue";
import Image from "./Image.vue";

const { data } = defineProps(["data"]);

const currImage = ref(0);
const prev = () => (currImage.value = currImage.value === 0 ? data.length - 1 : currImage.value - 1);
const next = () => (currImage.value = currImage.value === data.length - 1 ? 0 : currImage.value + 1);

const autoSlideInterval = 3000;
let autoSlideTimer;

const startAutoSlide = () => (autoSlideTimer = setInterval(() => next(), autoSlideInterval));
const stopAutoSlide = () => clearInterval(autoSlideTimer);

onMounted(startAutoSlide);
onUnmounted(stopAutoSlide);
</script>
