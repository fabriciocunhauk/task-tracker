<script>
    export default {
        props: {
            task: Object
        },
    }
</script>

<template>
    <li @dblclick="$emit('toggle-reminder', task.id)" :class="[task.reminder ? 'reminder' : ' ' ,'task']">
        <h3>
            {{ task.text }}
            <i @click="$emit('delete-task', task.id)" class="fas fa-solid fa-x"></i>
        </h3>
        <p>{{ task.day }}</p>
    </li>
</template>

<style scope>
.fas {
  color: red;
}

.task {
  background: #f4f4f4;
  margin: 5px 0 5px 0;
  padding: 10px 20px;
  cursor: pointer;
}

.task.reminder {
  border-left: 5px solid green;
}

.task h3 {
  display: flex;
  align-items: center;
  justify-content: space-between;
}
</style>