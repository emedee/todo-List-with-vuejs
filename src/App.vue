<template>
  <div id="app">
    <app-todo/>
  </div>
</template>

<script>
import Todo from '@/components/Todo.vue'
export default {
  name: 'app',
  components: {
      'app-todo': Todo
  }
}
</script>

<style>
#app {
  /* font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px; */
  background-color: black;
}
</style>
