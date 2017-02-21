<template>
  <div id="app">
    <!-- <img src="./assets/logo.png"> -->
    <todoList></todoList>
  </div>
</template>
<script>
import todoList from './components/todoList'

export default {
  name: 'app',
  components: {
    todoList
  }
}
</script>
<style>
#app {
  font-size: 14px;
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

body {
  display: flex;
  align-items: center;
  justify-content: center;
  height: 100%;
}
</style>
