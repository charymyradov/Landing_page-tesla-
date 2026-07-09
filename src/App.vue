<script>

import navbar from './components/navbar.vue';
import home from './components/home.vue';
import models from './components/models.vue';
import charging from './components/charging.vue';
import discover from './components/discover.vue';
import nfooter from './components/nfooter.vue';

export default {
  name: 'App',
  components: {
    navbar,
    home,
    models,
    charging,
    discover,
    
    nfooter,
  }
}
</script>

<template>
  <div>
    <navbar />
    <home />
    <models />
    <charging />
    <discover />
    
    <nfooter />
  </div>
</template>
