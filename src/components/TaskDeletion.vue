<template>
  <div>
    <h2>Delete Task</h2>
    <button @click="deleteAllTasks">Delete All Tasks</button>
  </div>
</template>

<script>
export default {
  methods: {
    deleteAllTasks() {
      this.$emit("delete-all-tasks");
    },
  },
};
</script>

<style scoped>
/* Add your CSS styles here */
button {
  background-color: #e74c3c;
  color: white;
  border: none;
  padding: 5px 10px;
  cursor: pointer;
}

button:hover {
  background-color: #c0392b;
}
</style>
