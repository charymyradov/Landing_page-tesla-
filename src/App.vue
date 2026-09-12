<script setup>
import navbar from './components/navbar.vue';
import home from './components/home.vue';
import models from './components/models.vue';
import charging from './components/charging.vue';
import discover from './components/discover.vue';
import nfooter from './components/nfooter.vue';
import BackToTop from './components/BackToTop.vue';
import LoadingSpinner from './components/LoadingSpinner.vue';
</script>

<template>
  <LoadingSpinner />
  <div>
    <navbar />
    <home />
    <models />
    <charging />
    <discover />
    <nfooter />
    <BackToTop />
  </div>
</template>
