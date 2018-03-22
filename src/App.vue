<template>
  <div id="app">
    <ToDoList :todos="todos" :addTodo="addTodo" />
  </div>
</template>

<script>
import ToDoList from './components/ToDoList.vue';

export default {
  name: 'app',
  data() {
    return {
      todos: [
        { task: 'Take out the trash' },
        { task: 'Be cool' },
        { task: 'Ride the train' },
        { task: 'Life' }
      ],
    };
  },
  methods: {
    addTodo(text) {
      const { todos } = this;
      return text.length ? todos.push({ task: text }) : alert('Please enter some text.')
    }
  },
  components: {
    ToDoList
  }
};
</script>

<style>
body {
  background: #edf0f5;
}

#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 60px;
  display: grid;
  grid-auto-flow: row;
  align-items: center;
  justify-items: center;
}

input,
button {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  font-size: 14px;
  color: #2c3e50;
  background: #edf0f5;
  border: none;
  border-radius: 3px;
}

input {
  height: 28px;
  width: 200px;
  margin-right: 10px;
}

button {
  height: 30px;
  width: 90px;
}
</style>
