<template>
  <div id="app">
    <h1>Task List App</h1>
    
    <task-creation @add-task="addTask"></task-creation>
    
    <task-filtering @filter-tasks="filterTasks"></task-filtering>
    
    <task-list :tasks="filteredTasks" @delete-task="deleteTask"></task-list>
    
    <task-deletion @delete-all-tasks="deleteAllTasks"></task-deletion>
  </div>
</template>

<script>
import TaskCreation from './components/TaskCreation.vue';
import TaskFiltering from './components/TaskFiltering.vue';
import TaskList from './components/TaskList.vue';
import TaskDeletion from './components/TaskDeletion.vue';

export default {
  components: {
    TaskCreation,
    TaskFiltering,
    TaskList,
    TaskDeletion
  },
  data() {
    return {
      tasks: [],
      filter: 'all'
    };
  },
  computed: {
    filteredTasks() {
      if (this.filter === 'all') {
        return this.tasks;
      } else if (this.filter === 'completed') {
        return this.tasks.filter(task => task.completed);
      } else {
        return this.tasks.filter(task => !task.completed);
      }
    }
  },
  methods: {
    addTask(title) {
      const newTask = {
        id: Date.now(),
        title: title,
        completed: false
      };
      this.tasks.push(newTask);
    },
    deleteTask(taskId) {
      const index = this.tasks.findIndex(task => task.id === taskId);
      if (index !== -1) {
        this.tasks.splice(index, 1);
      }
    },
    deleteAllTasks() {
      this.tasks = [];
    },
    filterTasks(filter) {
      this.filter = filter;
    }
  }
};
</script>

<style>
/* Add your global CSS styles here */
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 20px;
}

h1 {
  font-size: 2em;
}

/* Add more styles as needed */
</style>
