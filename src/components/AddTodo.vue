<template>
  <div>
    <form @submit.prevent="addTodo">
      <input type="text" v-model="title" name="title" placeholder="Add Todo...">
      <input type="submit" value="Submit" class="btn">
    </form>  
  </div>  
</template>

<script>
export default {
  name: 'AddTodo',
  data() {
    return {
      title: ''
    }
  },
  methods: {
    addTodo() {
      const newTodo = {
        title: this.title,
        completed: false
      };

      this.$emit('add-todo', newTodo);
      this.clearTodo();
    },
    clearTodo() {
      this.title = '';
    },
  }
}
</script>

<style lang="scss" scoped>
  form {
    display: flex;

    input[type="text"] {
      flex: 5;
      padding: 5px;
    }

    input[type="submit"] {
      flex: 1;
    }
  }
</style>