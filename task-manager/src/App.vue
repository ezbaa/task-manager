<script>
import Header from './components/Header.vue'
import Tasks from './components/Tasks.vue'
import AddTask from './components/AddTask.vue'

export default {
  name: 'App',
  components: {
    Header,
    Tasks,
    AddTask,
  },
  // function that returns an object
  data() {
    return {
      tasks: [],
      showAddTask: false,
    }
  },
  methods: {
    addTask(task) {
      this.tasks = [...this.tasks, task] //copies previous tasks and adds the new one
    },

    //Filtering out the method we want to "delete"
    deleteTask(id) {
      //parameter = id we want to
      if (confirm('Are you sure you want to delete this task?')) {
        this.tasks = this.tasks.filter((task) => task.id !== id) //returns every id except the one
      }
    },
    toggleReminder(id) {
      this.tasks = this.tasks.map((task) =>
        task.id === id ? { ...task, reminder: !task.reminder } : task,
      )
    },
    toggleAddTask() {
      this.showAddTask = !this.showAddTask
    },
  },
  // Lifecycle hook, called after component is initialized
  created() {
    // access the tasks above
    this.tasks = [
      {
        id: 1,
        text: 'appointment',
        day: 'march 1st at 2:30',
        reminder: true,
      },
      {
        id: 2,
        text: 'study',
        day: ' tomorrow at 9am',
        reminder: true,
      },
      {
        id: 3,
        text: 'carwash',
        day: 'Jan 5rd at 11:30',
        reminder: false,
      },
    ]
  },
}
</script>

<template>
  <div class="container">
    <Header @show-add-task="toggleAddTask" title="Task Tracker" :setAddTask="showAddTask" />
    <div v-show="showAddTask">
      <AddTask @add-task="addTask" />
    </div>
    <!-- Cathing the 'delete-task' and naming the mothod emit, 
     binding tasks to tasks data -->
    <Tasks @toggle-reminder="toggleReminder" @delete-task="deleteTask" :tasks="tasks" />
  </div>
</template>

<style>
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

.btn {
  display: inline-block;
  background: #000;
  color: #fff;
  border: none;
  padding: 10px 20px;
  margin: 5px;
  border-radius: 5px;
  cursor: pointer;
  text-decoration: none;
  font-size: 15px;
  font-family: inherit;
}

.btn:focus {
  outline: none;
}

.btn:active {
  transform: scale(0.98);
}

.btn-block {
  display: block;
  width: 100%;
}
</style>
