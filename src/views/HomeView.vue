<script>
  import MainHeader from '../components/HeaderMain.vue';
  import AddTaskForm from '../components/AddTaskForm.vue';
  import TasksList from '../components/TasksList.vue';

  export default {
    components: {
      MainHeader,
      AddTaskForm,
      TasksList
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
  <main>
    <div class="container">
      <MainHeader @button-click="toggleAddTask" title="Task Tracker" :showAddTask="showAddTask" />
      <div :class="[showAddTask ? 'form-container-transition' : 'form-container']" >
      <AddTaskForm @add-task="addTask" />
      </div>
      <TasksList 
        @toggle-reminder="toggleReminder" 
        @delete-task="deleteTask" 
        :tasks="tasks" 
      />
    </div>
  </main>
</template>

<style scope>
main {
  display: flex;
  justify-content: center;
}

.form-container {
  height: 0;
  overflow-y: auto;
  transition-duration: .3s;
}

.form-container-transition {
  height: 300px;
  transition-duration: .3s;
}

.container {
  max-width: 500px;
  overflow: auto;
  min-height: 300px;
  border: 1px solid steelblue;
  padding: 30px;
  border-radius: 5px;
  margin: 16px;
}
</style>
