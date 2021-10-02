<template>
  <div>
    <div v-for="todo in todos" :key="todo.id">
      <TodoItem :todo="todo" @del-todo="delTodo" />
    </div>
  </div>
</template>

<script>
import TodoItem from './TodoItem';

export default {
  name: 'Todos',
  components: {
    TodoItem
  },
  props: ['todos'],
  methods: {
    delTodo(id) {
      this.$emit('del-todo', id);
    }
  }
}
</script>

<style lang="scss" scoped>
  
</style>