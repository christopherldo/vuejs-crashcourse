<template>
  <div class="todo-item" :class="{'is-complete':todo.completed}">
    <div class="info">
      <input type="checkbox" @change="markComplete" :checked="todo.completed ? 'true' : false">
      <p>{{ todo.title }}</p>
    </div>
    <div class="delete">
      <button @click="delTodo(todo.id)" class="del">x</button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'TodoItem',
  props: ['todo'],
  methods: {
    markComplete() {
      this.todo.completed = !this.todo.completed;
    },
    delTodo(id) {
      this.$emit('del-todo', id);
    }
  }
}
</script>

<style lang="scss" scoped>
  .todo-item {
    display: flex;
    justify-content: space-between;
    background: #f4f4f4;
    padding: 10px;
    border-bottom: 1px #ccc dotted;

    &.is-complete {
      text-decoration: line-through;
    }

    .info {
      display: flex;
      align-items: center;

      input {
        margin-right: 10px;
      }
    }

    .del {
      background: #ff0000;
      color: #fff;
      border: none;
      padding: 5px 9px;
      border-radius: 50%;
      cursor: pointer;
    }
  }
</style>