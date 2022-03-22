<template>
  <div class="container">
    <div class="row justify-content-center">
      <div class="col-12 col-md-8 col-xl-5 border rounded-3 shadow-sm p-3">
        <Header @toggle-add-task="toggleAddTask" title="Task Tracker" :showAddTask="showAddTask" />
        <div v-show="showAddTask">
          <AddTask @add-task="saveTask" />
        </div>
        <Tasks @toggle-reminder="toggleReminder" @delete-task="deleteTask" :tasks="tasks" />
      </div>
    </div>
  </div>
</template>

<style>
    .rounded-3{
      border-radius: 1rem !important
    }
</style>

<script>

import Header from './components/Header';
import Tasks from './components/Tasks'
import AddTask from './components/AddTask'

export default {
  name: 'App',
  components: {
    AddTask,
    Header,
    Tasks
  },
  data(){
    return {
      tasks: [],
      showAddTask: false
    }
  },
  created(){
    this.tasks = [
      {
        'id': 1,
        'title': 'Doctor\'s appointment',
        'day': 'March 1st at 2:30pm',
        'reminder': true
      },
      {
        'id': 2,
        'title': 'Meeting at School',
        'day': 'March 3rd at 1:30pm',
        'reminder': false
      },
      {
        'id': 3,
        'title': 'Food shopping',
        'day': 'March 3rd at 11:00am',
        'reminder': true
      }
    ]
  },
  methods: {
    saveTask(task){
      this.tasks = [...this.tasks, task];
    },
    deleteTask(id){
      if(confirm('Are you sure that you want to delete this task?')){
        this.tasks = this.tasks.filter((task) => task.id !== id)
      }
    },
    toggleReminder(id){
      this.tasks = this.tasks.map(
        (task) => task.id === id ? {...task, reminder: !task.reminder} : task
      )
    },
    toggleAddTask(){
      this.showAddTask = !this.showAddTask
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
