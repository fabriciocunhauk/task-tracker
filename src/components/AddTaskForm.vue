<script>
import ButtonMain from './ButtonMain.vue'
export default {
  data() {
    return {
      text: '',
      day: '',
      reminder: false
    }
  },
  components: {
    ButtonMain
  },
  methods: {
    async onSubmit(event) {
      event.preventDefault()
      if (!this.text) {
        alert('Please Add a Task')
        return
      }

      const newTask = {
        text: this.text,
        day: this.day,
        reminder: this.reminder
      }

      this.$emit('add-task', newTask);
      
      this.text = ''
      this.day = ''
      this.reminder = false
    }
  }
}
</script>

<template>
  <form @submit="onSubmit" class="add-form">
    <div class="form-control">
      <label>Task</label>
      <input type="text" v-model="text" name="text" placeholder="Add Task" />
    </div>
    <div class="form-control">
      <label>Day & Time</label>
      <input type="text" v-model="day" name="day" placeholder="Add Day & Time" />
    </div>
    <div class="form-control-check">
      <label>Set Reminder</label>
      <input type="checkbox" v-model="reminder" name="reminder" />
    </div>
    <ButtonMain type="submit" class="btn btn-block" text="Save Task" />
  </form>
</template>

<style scoped>
.form-control {
  margin: 20px 0;
}

.form-control label {
  display: block;
}

.form-control input {
  width: 100%;
  height: 40px;
  padding: 3px 7px;
  font-size: 17px;
}

.form-control-check {
  width: 100%;
  margin-bottom: 20px;
  display: flex;
  align-items: center;
  justify-content: space-between;
}

.form-control-check label {
  flex: 1;
}

.form-control-check input {
  width: 20px;
  height: 20px;
}
</style>
