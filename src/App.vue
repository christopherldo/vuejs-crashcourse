<template>
  <div id="app">
    <Header />
    <AddTodo @add-todo="addTodo"/>
    <Todos :todos="todos" @del-todo="deleteTodo"/>
  </div>
</template>

<script>
import {v4 as uuid} from 'uuid';

import Header from './components/layout/Header';
import Todos from './components/Todos';
import AddTodo from './components/AddTodo';

export default {
  name: 'App',
  components: {
    Header,
    Todos,
    AddTodo,
  },
  data() {
    return {
      todos: [
        {
          id: uuid(),
          title: 'Todo One',
          completed: false,
        },
        {
          id: uuid(),
          title: 'Todo Two',
          completed: true,
        },
        {
          id: uuid(),
          title: 'Todo Three',
          completed: false,
        },
      ],
    };
  },
  methods: {
    deleteTodo(id) {
      this.todos = this.todos.filter(todo => todo.id !== id);
    },
    addTodo(newTodo) {
      newTodo.id = uuid();
      this.todos.push(newTodo);
    },
  },
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
