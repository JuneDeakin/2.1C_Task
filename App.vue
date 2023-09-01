<template>
<div class="centered">
  <img alt="Vue logo" src="./assets/logo.png" class="logo">  
  <div class="todo-app">
    <h1>Todo App</h1>
    <input v-model="newTask" @keyup.enter="addTask" placeholder="Enter a new task">
    <ul>
      <li v-for="(task, index) in tasks" :key="index">
        <div class="task-item"></div>
        <input type="checkbox" v-model="task.completed">
        <span :class="{ completed: task.completed}">{{ task.text }}</span>
        <button @click="removeTask(index)">Remove</button>
      </li>
    </ul>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      newTask: '',
      tasks: []
    };
  },
  methods: {
    addTask() {
      if (this.newTask.trim() !== '') {
        this.tasks.push({
          text: this.newTask,
          completed: false
        });
        this.newTask = '';
      }
    },
    removeTask(index) {
      this.tasks.splice(index, 1);
    }
  }
};
</script>

<style scoped>
.centered {
  display: flex;
  justify-content: center;
  align-items: center;
  min-height: 100vh;
  flex-direction: column;
}
.logo {
  max-width: 200px;
  margin-bottom: 20px;
}
.todo-app {
  text-align: center;
  padding: 20px;
  border: 1px solid #ccc;
  background-color: #f9f9f9;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
  max-width: 400px;
}
.task-item {
  display: flex;
  align-items: center;
  margin-bottom: 10px;
}
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
