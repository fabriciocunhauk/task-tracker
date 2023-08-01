<script>
import MainHeader from '../components/HeaderMain.vue'
import AddTaskForm from '../components/AddTaskForm.vue'
import TasksList from '../components/TasksList.vue'

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
  async created() {
    this.tasks = await this.fetchTasks()
  },
  methods: {
    async addTask(task) {
      const url = 'http://localhost:3000/tasks'

      const taskToAdd = {
        method: 'POST',
        headers: { 'Content-Type': 'application/json' },
        body: JSON.stringify(task)
      }

      await fetch(url, taskToAdd)

      this.tasks = [...this.tasks, task]
    },
    async deleteTask(id) {
      const url = `http://localhost:3000/tasks/${id}`

      const res = await fetch(url, {
        method: 'DELETE'
      })

      res.status === 200
        ? (this.tasks = this.tasks.filter((task) => task.id !== id))
        : alert('Error deleting task try again')
    },
    toggleAddTask() {
      this.showAddTask = !this.showAddTask
    },
    toggleReminder(id) {
      this.tasks = this.tasks.map((task) =>
        task.id === id ? { ...task, reminder: !task.reminder } : task
      )
    },
    async fetchTasks() {
      const url = 'http://localhost:3000/tasks'
      const data = await fetch(url)
        .then((response) => response.json())
        .then((tasks) => {
          return (this.tasks = tasks)
        })

      return data
    }
  }
}
</script>

<template>
  <main>
    <div class="container">
      <MainHeader @button-click="toggleAddTask" title="Task Tracker" :showAddTask="showAddTask" />
      <div :class="[showAddTask ? 'form-container-transition' : 'form-container']">
        <AddTaskForm @add-task="addTask" />
      </div>
      <TasksList @toggle-reminder="toggleReminder" @delete-task="deleteTask" :tasks="tasks" />
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
  transition-duration: 0.3s;
}

.form-container-transition {
  height: 300px;
  transition-duration: 0.3s;
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
