<template>
  <div id="app">
    <AddTodo @add-todo="addTodo"/>
    <Todos :todos="todos" @del-todo="deleteTodo"/>
  </div>
</template>

<script>
import axios from 'axios';

import Todos from '../components/Todos';
import AddTodo from '../components/AddTodo';

export default {
  name: 'Home',
  components: {
    Todos,
    AddTodo,
  },
  data() {
    return {
      todos: [],
    };
  },
  methods: {
    deleteTodo(id) {
      try {
        axios.delete(`https://jsonplaceholder.typicode.com/todos/${id}`);
        this.todos = this.todos.filter(todo => todo.id !== id);
      } catch (error) {
        console.log(error);
      }
    },
    async addTodo(newTodo) {
      const { title, completed } = newTodo;

      try {
        const { data } = await axios.post(
          'https://jsonplaceholder.typicode.com/todos',
          { title, completed },
        );
        this.todos.push(data);
      } catch (error) {
        console.log(error);
      }
    },
    async getAllTodos() {
      try {
        const response = await axios.get(
          'https://jsonplaceholder.typicode.com/todos?_limit=5'
        );
        this.todos = response.data;
      } catch (error) {
        console.log(error);
      }
    }
  },
  created() {
    this.getAllTodos();
  }
}
</script>

<style>
  * {
    box-sizing: border-box;
    margin: 0;
    padding: 0;
  }

  body {
    font-family: Arial, Helvetica, sans-serif;
    line-height: 1.4;
  }

  .btn {
    display: inline-block;
    border: none;
    background: #555;
    color: #fff;
    padding: 7px 20px;
    cursor: pointer;
  }
</style>
