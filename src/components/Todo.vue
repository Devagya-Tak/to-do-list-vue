<template>
    <div class="container bg-light p-3">
      <h1>Todo List</h1>
      <form @submit.prevent="addTodo">
        <div class="input-group mb-3">
          <input v-model="newTodo" type="text" class="form-control" placeholder="Add a new todo" required>
          <button type="submit" class="btn btn-primary">Add</button>
        </div>
      </form>
      <ul class="list-group">
        <li v-for="(todo, index) in todos" :key="index" class="list-group-item">
          {{ todo }}
          <button class="btn btn-danger btn-sm float-right" @click="removeTodo(index)">Remove</button>
        </li>
      </ul>
    </div>
  </template>
  
  <script setup>
  import { ref } from 'vue';
  
  const newTodo = ref('');
  const todos = ref([]);
  
  const addTodo = () => {
    if (newTodo.value.trim() !== '') {
      todos.value.push(newTodo.value.trim());
      newTodo.value = ''; // Clear the input after adding a todo
    }
  };
  
  const removeTodo = (index) => {
    todos.value.splice(index, 1);
  };
  </script>
  
  <style scoped>
  .container {
    border-radius: 3px;
    margin-top: auto;
    margin-left: auto;
  }
  /* Add your component-specific styles here */
  </style>
  