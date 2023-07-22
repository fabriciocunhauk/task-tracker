<script>
import TaskItem from './TaskItem.vue';

    export default {
        components: {
            TaskItem            
        },
        props: {
            tasks: Array
        },
        emits: ['delete-task', 'toggle-reminder']
    }
</script>

<template>
    <ul :key="task.id" v-for="task in tasks">
        <TaskItem 
            @toggle-reminder="$emit('toggle-reminder', task.id)" 
            @delete-task="$emit('delete-task', task.id)" 
            :task="task" 
        />
    </ul>
</template>