<template>
  <div class="container">
    <Header title="Task Tracker"></Header>
    <AddTask @add-task="addTask" />
    <Tasks 
      @toggle-reminder="toggleReminder"
      @delete-task="deleteTask" 
      :tasks="tasks"></Tasks>
  </div>
</template>

<script>
import Header from './components/Header'
import Tasks from './components/Tasks'
import AddTask from './components/AddTask'

export default {
  name: 'App',

  components: {
    Header,
    Tasks,
    AddTask
  },

  data() {
    return {
      tasks: []
    }
  },
  methods: {
    addTask(newTask) {
      this.tasks = [...this.tasks, newTask]
    },

    deleteTask(id) {
      this.tasks = this.tasks.filter((task) => task.id != id)
    },

    toggleReminder(id) {
      this.tasks = this.tasks.map(
        (task) => task.id === id ? 
        {...task, reminder: !task.reminder} :
        task
      )
    }
  },
  created() {
    this.tasks = [
      {
        id: 1,
        text: 'ITFM Meeting',
        day: 'March 27 at 6.30pm',
        reminder: true
      },
      {
        id: 2,
        text: 'AntiCafe Chill',
        day: 'March 23 at 5.20pm',
        reminder: true
      },
      {
        id: 3,
        text: 'Birthday Party',
        day: 'April 23 at 7.00pm',
        reminder: false
      }
    ]
  }
}
</script>

<style>
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
  max-width: 480px;
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
