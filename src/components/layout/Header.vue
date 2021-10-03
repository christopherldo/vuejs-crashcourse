<template>
  <header class="header">
    <h1>TodoList</h1>
    <div id="nav">
      <router-link to="/">Home</router-link>
      <router-link to="/about">About</router-link>
    </div>
  </header>
</template>

<script>
export default {
  name: 'Header'
}
</script>

<style lang="scss" scoped>
  .header {
    background: #333;
    color: #fff;
    text-align: center;
    padding: 10px;

    a {
      color: #fff;
      margin-right: 5px;
      padding-bottom: 2px;
      text-decoration: none;
      transition: all 0.3s ease-in-out 0s;

      &:hover {
        color: #aaa;

        &.router-link-exact-active {
          border-color: #aaa;
        }
      }

      &.router-link-exact-active {
        border-bottom: 1px solid #fff;
      }
    }
  }
</style>