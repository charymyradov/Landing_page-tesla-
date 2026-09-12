<template>
  <div class="fixed inset-0 z-[100] flex items-center justify-center bg-black transition-opacity duration-500"
       :class="loaded ? 'opacity-0 pointer-events-none' : 'opacity-100'">
    <div class="flex flex-col items-center gap-4">
      <svg class="animate-spin h-12 w-12 text-white" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24">
        <circle class="opacity-25" cx="12" cy="12" r="10" stroke="currentColor" stroke-width="4"></circle>
        <path class="opacity-75" fill="currentColor" d="M4 12a8 8 0 018-8V0C5.373 0 0 5.373 0 12h4z"></path>
      </svg>
      <p class="text-white text-sm audiowide-regular tracking-widest">TESLA</p>
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue';

const loaded = ref(false);

onMounted(() => {
  window.addEventListener('load', () => {
    setTimeout(() => {
      loaded.value = true;
    }, 300);
  });
  if (document.readyState === 'complete') {
    setTimeout(() => {
      loaded.value = true;
    }, 300);
  }
});
</script>
