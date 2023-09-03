<template>
    <div class="task-list">
      <h2>Task List</h2>
      <ul>
        <!-- Loop through tasks and display them -->
        <li v-for="task in tasks" :key="task.id">
          <div class="task-item">
            <span class="task-name">{{ task.name }}</span>
            <span class="due-date">Due Date: {{ task.dueDate }}</span>
            <span class="task-description">{{ task.description }}</span>
            <button @click="markAsCompleted(task.id)">Mark as Completed</button>
            <button @click="deleteTask(task.id)">Delete</button>
          </div>
        </li>
      </ul>
    </div>
  </template>
  
  <script>
  export default {
    props: {
      tasks: Array, // An array of task objects
    },
    methods: {
      markAsCompleted(taskId) {
        // Add logic to mark a task as completed
        this.$emit("mark-completed", taskId);
      },
      deleteTask(taskId) {
        // Add logic to delete a task
        this.$emit("delete-task", taskId);
      },
    },
  };
  </script>
  
  <style scoped>
  .task-list {
    max-width: 600px;
    margin: 0 auto;
  }
  
  h2 {
    font-size: 1.5rem;
  }
  
  ul {
    list-style-type: none;
    padding: 0;
  }
  
  li {
    border: 1px solid #ddd;
    padding: 10px;
    margin-bottom: 10px;
    background-color: #fff;
    border-radius: 5px;
  }
  
  .task-item {
    display: flex;
    flex-direction: column;
  }
  
  .task-name {
    font-weight: bold;
  }
  
  .due-date {
    color: #888;
  }
  
  .task-description {
    margin-top: 10px;
  }
  
  button {
    margin-top: 10px;
    padding: 5px 10px;
    background-color: #007bff;
    color: #fff;
    border: none;
    border-radius: 5px;
    cursor: pointer;
  }
  
  button:hover {
    background-color: #0056b3;
  }
  </style>
  