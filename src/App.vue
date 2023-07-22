<script setup>
import { RouterView } from 'vue-router';
import HelloWorld from './components/HelloWorld.vue'
</script>

<template>
  <header>
    <div class="wrapper">
      <HelloWorld msg="You did it!" />
    </div>
  </header>

  <RouterView />
</template>

<style scoped>
header {
  line-height: 1.5;
  max-height: 100vh;
}

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }
</style>
