<script>
  import { RouterView } from 'vue-router';
  import HomeView from './views/HomeView.vue';
  import TasksList from './components/TasksList.vue';

  export default {
    components: {
      HomeView,
      RouterView,
      TasksList
    },
    data() {
      return {
        tasks: []
      }
    },
    methods: {
      deleteTask(id) {
        this.tasks = this.tasks.filter(task => task.id !== id)
      },
      toggleReminder(id) {
        console.log("Toggle");
        this.tasks = this.tasks.map(task => task.id === id ? {...task, reminder: !task.reminder} : task)
      }
    },
    created() {
      this.tasks = [
        {
          id: 1,
          text: "Doctors Appointment",
          day: " March 1st at 2:30pm",
          reminder: true
        },
        {
          id: 2,
          text: "Meeting as School",
          day: " March 1st at 1:30pm",
          reminder: true
        },
        {
          id: 3,
          text: "Food Shopping",
          day: "January 7th at 5:30pm",
          reminder: false
        },
      ]
    }
  }
</script>

<template>
  <header>
    <div class="container">
      <HomeView />
      <TasksList 
      @toggle-reminder="toggleReminder" 
      @delete-task="deleteTask" 
      :tasks="tasks" 
      />
    </div>
  </header>

  <RouterView />
</template>

<style scoped>
  @import url('https://fonts.googleapis.com/css2?family=Poppins:wght@300;400&display=swap');

* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

body {
  font-family: 'Poppins', sans-serif;
}

.container {
  max-width: 500px;
  margin: 30px auto;
  overflow: auto;
  min-height: 300px;
  border: 1px solid steelblue;
  padding: 30px;
  border-radius: 5px;
}
</style>
