<template>
  <img :src="src" :alt="alt" :class="classes" class="object-cover w-full h-full rounded-lg" />
</template>

<script setup>
defineProps(["src", "alt", "classes"]);
</script>
