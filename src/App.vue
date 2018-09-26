<template>
  <div id="app">
    <ToDoList v-if="!showCompleted" :todos="todos" :addTodo="addTodo" :completeTodo="completeTodo" />
    <Completed v-if="!!showCompleted" :completed="completed" />
  </div>
</template>

<script>
import ToDoList from './components/ToDoList.vue';
import Completed from './components/Completed.vue';

const uuidv4 = () => {
  return ([1e7] + -1e3 + -4e3 + -8e3 + -1e11).replace(/[018]/g, c =>
    // eslint-disable-next-line
    (
      c ^
      (crypto.getRandomValues(new Uint8Array(1))[0] & (15 >> (c / 4)))
    ).toString(16)
  );
};

export default {
  name: 'app',
  data() {
    return {
      todos: [
        { id: '5092f9jseanv', task: 'Take out the trash' },
        { id: '39r20afjslsl', task: 'Be cool' },
        { id: '12049asfddls', task: 'Ride the train' },
        { id: '03289fj3i3il', task: 'Life' },
        { id: '6if993fsjlkl', task: 'Other stuff' },
        {
          id: '85583asdfkje',
          task: 'A really long task that will take up more space on the screen'
        },
        { id: '217t13sldkjj', task: 'A task that should be below the fold?' }
      ],
      completed: [],
      showCompleted: false
    };
  },
  methods: {
    addTodo(text) {
      return text.length
        ? (this.todos = [{ id: uuidv4(), task: text }, ...this.todos])
        : alert('Please enter some text.');
    },
    completeTodo(id) {
      let found = this.todos.find(todo => todo.id === id);
      (this.completed = [found, ...this.completed]);
      return this.todos = this.todos.filter(todo => todo.id !== id);
    }
  },
  components: {
    ToDoList,
    Completed
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
