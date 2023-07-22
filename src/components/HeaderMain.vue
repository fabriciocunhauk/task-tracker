<script setup>
import ButtonMain from './ButtonMain.vue';

defineProps({
  title: {
    type: String,
  }
})
</script>

<template>
  <header class="greetings">
    <h1>{{ title }}</h1>
    <ButtonMain text="Add Task" />
  </header>
</template>

<style scoped>
  header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-bottom: 20px;
  }
</style>
