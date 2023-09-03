<template>
    <div class="task-form">
      <h2>Add Task</h2>
      <form @submit.prevent="addTask">
        <div class="form-group">
          <label for="taskName">Task Name:</label>
          <input
            type="text"
            id="taskName"
            v-model="taskName"
            placeholder="Enter task name"
            required
          />
        </div>
        <div class="form-group">
          <label for="dueDate">Due Date:</label>
          <input type="date" id="dueDate" v-model="dueDate" required />
        </div>
        <div class="form-group">
          <label for="taskDescription">Description:</label>
          <textarea
            id="taskDescription"
            v-model="taskDescription"
            placeholder="Enter task description"
          ></textarea>
        </div>
        <button type="submit" class="add-task-btn">Add Task</button>
      </form>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        taskName: "",
        dueDate: "",
        taskDescription: "",
      };
    },
    methods: {
      addTask() {
        // Add logic to handle task creation here
        const newTask = {
          name: this.taskName,
          dueDate: this.dueDate,
          description: this.taskDescription,
        };
  
        // Emit an event or call a method to add the new task to the task list
        this.$emit("add-task", newTask);
  
        // Clear form fields
        this.taskName = "";
        this.dueDate = "";
        this.taskDescription = "";
      },

      markTaskCompleted(taskId) {
      // Implement logic to mark a task as completed based on taskId
      // For example, update the task status in the tasks array
      const taskIndex = this.tasks.findIndex((task) => task.id === taskId);
      if (taskIndex !== -1) {
        this.tasks[taskIndex].completed = true;
      }
    },

    deleteTask(taskId) {
      // Find the index of the task to delete
      const taskIndex = this.tasks.findIndex((task) => task.id === taskId);
      
      if (taskIndex !== -1) {
        // Remove the task from the tasks array
        this.tasks.splice(taskIndex, 1);
      }
    }
    },
  };
  </script>
  
  <style scoped>
  .task-form {
    max-width: 400px;
    margin: 0 auto;
    padding: 20px;
    background-color: #f9f9f9;
    border: 1px solid #ddd;
    border-radius: 5px;
  }
  
  .form-group {
    margin-bottom: 15px;
  }
  
  label {
    display: block;
    font-weight: bold;
  }
  
  input[type="text"],
  input[type="date"],
  textarea {
    width: 100%;
    padding: 10px;
    border: 1px solid #ccc;
    border-radius: 5px;
  }
  
  button.add-task-btn {
    display: block;
    width: 100%;
    padding: 10px;
    background-color: #007bff;
    color: #fff;
    border: none;
    border-radius: 5px;
    cursor: pointer;
  }
  
  button.add-task-btn:hover {
    background-color: #0056b3;
  }
  </style>
  