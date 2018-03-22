<template>
  <div id="app">
    <ToDoList :todos="todos"/>
  </div>
</template>

<script>
import ToDoList from './components/ToDoList.vue'

export default {
  name: 'app',
  data() {
    return {
      todos: [
        { task: 'Take out the trash'},
        { task: 'Be cool'},
        { task: 'Ride the train'},
        { task: 'Life'}
      ]
    }
  },
  components: {
    ToDoList
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
