<template>
  <div id="app">
    <form @submit.prevent="addTodo">
      <input v-model="text">
      <button>Add Todo</button>
    </form>
    <ToDoList :todos="todos"/>
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
      text: ''
    };
  },
  methods: {
    addTodo() {
      const { text, todos } = this;
      return text.length ? todos.push({ task: text }) : alert('Please enter some text.')
    }
  },
  components: {
    ToDoList
  }
};
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

form,
input,
button {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  font-size: 14px;
  color: #2c3e50;
}

button {
  border: none;
  border-radius: 3px;
  height: 30px;
  width: 90px;
}
</style>
