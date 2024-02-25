<template>
  <div ref="container" @mouseenter="handleMouseEnter" class="relative inline-block tooltip group">
    <slot></slot>
    <span
      ref="tooltipRef"
      v-if="tooltip"
      class="tooltiptext absolute invisible min-w-[120px] max-w-[250px] px-2 py-1 text-center mt-2 text-white transition shadow-md bg-neutral-800 rounded-lg opacity-0 group-hover:visible group-hover:opacity-100 top-[60%]"
    >
      {{ tooltip }}
    </span>
  </div>
</template>

<script setup>
import { ref } from "vue";

const props = defineProps(["tooltip"]);

const tooltipRef = ref(null);
const container = ref(null);

const handleMouseEnter = (event) => {
  if (!tooltipRef.value || !container.value) return;

  const { width: tooltipWidth } = tooltipRef.value.getBoundingClientRect();
  const leftPosition = (event.target.offsetWidth - tooltipWidth) / 2;
  tooltipRef.value.style.left = `${leftPosition}px`;
};
</script>

<style scoped>
.tooltip .tooltiptext::before {
  content: "";
  position: absolute;
  bottom: 100%;
  left: 50%;
  margin-left: -7px;
  border-width: 7px;
  border-style: solid;
  border-color: transparent transparent #262626 transparent;
}
</style>
