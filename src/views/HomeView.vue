<script>
  import MainHeader from '../components/HeaderMain.vue';

  export default {
    components: {
      MainHeader
    },
    props: {
            showAddTask: Boolean
        },
  }
</script>

<template>
  <main>
    <MainHeader @button-click="$emit('button-click')" title="Task Tracker" :showAddTask="showAddTask" />
  </main>
</template>
