<template>
    <div>
      <h2>Task List</h2>
      <ul>
        <transition-group name="fade" tag="ul">
          <li v-for="task in tasks" :key="task.id" :class="{ completed: task.completed }">
            <span>{{ task.title }}</span>
            <div class="button-container">
              <button @click="deleteTask(task.id)">Delete</button>
              <button @click="completeTask(task)">Complete</button>
              <transition name="fade">
                <div class="checkmark" v-if="task.completed">&#10003;</div>
              </transition>
            </div>
          </li>
        </transition-group>
      </ul>
    </div>
  </template>
  
  <script>
  export default {
    props: {
      tasks: Array,
    },
    methods: {
      deleteTask(taskId) {
        this.$emit("delete-task", taskId);
      },
      completeTask(task) {
        task.completed = true;
      },
    },
  };
  </script>
  
  <style scoped>
  /* Add your CSS styles here */
  
  /* Default styles for larger screens */
  ul {
    list-style-type: none;
    padding: 0;
  }
  
  li {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 10px;
    border: 1px solid #ccc;
    margin: 5px 0;
    transition: opacity 0.3s; /* Fade transition */
  }
  
  .completed {
    background-color: #3498db; /* Blue background for completed tasks */
  }
  
  .button-container {
    display: flex;
    gap: 10px; /* Adjust the gap between buttons as needed */
  }
  
  button {
    background-color: #ff5733;
    color: white;
    border: none;
    padding: 5px 10px;
    cursor: pointer;
  }
  
  button:hover {
    background-color: #e54e2a;
  }
  
  /* Animation */
  .fade-enter-active,
  .fade-leave-active {
    transition: opacity 0.3s;
  }
  .fade-enter, .fade-leave-to /* .fade-leave-active in <2.1.8 */ {
    opacity: 0;
  }
  
  .checkmark {
    font-size: 20px;
    color: white; /* Set text color to white for better visibility */
    background-color: #3498db; /* Blue background for the checkmark */
    display: inline-block;
    transition: transform 0.3s; /* Add a transition for the checkmark */
  }
  
  /* Hover effect for the checkmark */
  .checkmark:hover {
    transform: scale(1.2);
  }
  
  /* Responsive design for smaller screens (e.g., mobile) */
  @media screen and (max-width: 768px) {
    li {
      flex-direction: column; /* Stack elements vertically */
    }
    
    .button-container {
      flex-direction: row; /* Place buttons side by side */
      margin-top: 10px; /* Add some space between the buttons and the task title */
    }
    
    .checkmark {
      margin-top: 10px; /* Add space between the checkmark and task title */
    }
  }
  </style>
  