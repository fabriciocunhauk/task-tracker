<script setup>
import ButtonMain from './ButtonMain.vue';

defineProps({
  title: {
    type: String,
  },
  showAddTask: {
    type: Boolean
  }
})
</script>

<template>
  <header class="greetings">
    <h1>{{ title }}</h1>
    <ButtonMain 
      @button-click="$emit('button-click')" 
      :text="showAddTask ? 'Close' : 'Add Task'" 
      :color="showAddTask ? 'red' : 'green'" 
    />
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
