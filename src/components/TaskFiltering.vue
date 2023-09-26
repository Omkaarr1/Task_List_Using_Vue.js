<template>
  <div>
    <h2>Filter Tasks</h2>
    <label for="filter">Filter:</label>
    <select v-model="selectedFilter" id="filter">
      <option value="all">All</option>
      <option value="completed">Completed</option>
      <option value="incomplete">Incomplete</option>
    </select>
  </div>
</template>

<script>
export default {
  data() {
    return {
      selectedFilter: "all",
    };
  },
  watch: {
    selectedFilter(newValue) {
      this.$emit("filter-tasks", newValue);
    },
  },
};
</script>

<style scoped>
/* Add your CSS styles here */
select {
  padding: 5px;
  border: 1px solid #ccc;
}
</style>
