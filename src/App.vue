<script>
  import HomeView from './views/HomeView.vue';
  import TasksList from './components/TasksList.vue';
  import AddTaskForm from './components/AddTaskForm.vue';

  export default {
    components: {
      HomeView,
      TasksList,
      AddTaskForm
    },
    data() {
      return {
        tasks: [],
        showAddTask: false
      }
    },
    methods: {
      toggleAddTask() {
        this.showAddTask = !this.showAddTask
      },
      addTask(task) {
        this.tasks = [...this.tasks, task];
      },
      deleteTask(id) {
        this.tasks = this.tasks.filter(task => task.id !== id)
      },
      toggleReminder(id) {
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
  <div class="wrapper">
    <div class="container">
      <HomeView 
        @button-click="toggleAddTask" 
        :showAddTask="showAddTask"
      />
      <div v-if="showAddTask">
      <AddTaskForm @add-task="addTask" />
      </div>
      <TasksList 
        @toggle-reminder="toggleReminder" 
        @delete-task="deleteTask" 
        :tasks="tasks" 
      />
    </div>
  </div>
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

.wrapper {
  display: flex;
  align-items: center;
  justify-content: center;
  width: 100%;
  height: 100vh;
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
