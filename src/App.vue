<template>
  <div>
    <header>
      <h1>Task Tracker</h1>
    </header>
    <main>
      <!-- Include the TaskList component and pass tasks as a prop -->
      <TaskList :tasks="tasks" @mark-completed="markTaskCompleted" @delete-task="deleteTask"/>
      <!-- Include the TaskForm component and listen for the "add-task" event -->
      <TaskForm @add-task="addTask" />
    </main>
  </div>
</template>

<script>
import TaskList from './components/TaskList.vue';
import TaskForm from './components/TaskForm.vue';

export default {
  components: {
    TaskList,
    TaskForm
  },
  data() {
    return {
      tasks: [] // Initialize an empty array to store tasks
    };
  },
  methods: {
    addTask(newTask) {
      // Push the new task into the tasks array
      this.tasks.push(newTask);

      

    }
  }
};
</script>


