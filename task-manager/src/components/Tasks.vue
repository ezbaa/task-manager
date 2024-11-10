<template>
  <!-- Looping through the tasks, u should add key to v-bind -->
  <div :key="task.id" v-for="task in tasks">
    <!-- cathing the 'delete-task method from Task' and sending it forward to App -->
    <Task
      @toggle-reminder="$emit('toggle-reminder', task.id)"
      @delete-task="$emit('delete-task', task.id)"
      :task="task"
    />
    <!-- Displaying tasks list -->
  </div>
</template>

<script>
import Task from './Task.vue'

export default {
  name: 'Tasks',
  props: {
    tasks: Array,
  },
  components: {
    Task,
  },
  emits: ['delete-task', 'toggle-reminder'], // have to define the emit
}
</script>
