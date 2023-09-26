<template>
  <div>
    <h2>Create Task</h2>
    <div class="task-input">
      <input v-model="newTask" placeholder="Enter task title" />
      <button @click="addTask">Add Task</button>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      newTask: "",
    };
  },
  methods: {
    addTask() {
      if (this.newTask.trim() === "") {
        alert("Task title cannot be empty");
        return;
      }
      this.$emit("add-task", this.newTask);
      this.newTask = "";
    },
  },
};
</script>

<style scoped>
/* Add your CSS styles here */
.task-input {
  display: flex;
  align-items: center;
}

input {
  flex-grow: 1;
  padding: 5px;
  border: 1px solid #ccc;
  margin-right: 10px;
}

button {
  background-color: #2ecc71;
  color: white;
  border: none;
  padding: 5px 10px;
  cursor: pointer;
}

button:hover {
  background-color: #27ae60;
}
</style>
