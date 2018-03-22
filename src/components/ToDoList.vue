<template>
  <div class="todos-container">
    <form @submit.prevent="addTodo(inputText)">
      <input v-model="inputText">
      <button>Add Todo</button>
    </form>
    <ul>
      <li class="todo" v-for="todo in todos" :key="todo.task">{{todo.task}}</li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'ToDoList',
  props: {
    todos: Array,
    addTodo: Function,
  },
  data() {
    return {
      inputText: ''
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}

ul {
  list-style-type: none;
  padding: 0;
  display: grid;
  grid-auto-flow: row;
  max-height: 265px;
  overflow-y: scroll;
}

.todo {
  padding: 10px;
}

.todo:nth-child(odd) {
  background: #edf0f5;
}

a {
  color: #42b983;
}

.todos-container {
  background: #fff;
  width: 50%;
  min-height: 250px;
  padding: 16px;
  border-radius: 3px;
  box-shadow: 0px 1px 1px 0px rgba(0, 0, 0, 0.75);
}
</style>
