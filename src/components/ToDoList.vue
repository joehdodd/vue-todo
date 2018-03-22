<template>
  <div class="todos-container">
    <form @submit.prevent="addTodo(inputText)">
      <input v-model="inputText">
      <button>Add Todo</button>
    </form>
    <ul>
      <li class="todo" v-for="todo in todos" :key="todo.task">
        <span class="todo-task">{{todo.task}}</span>
        <span class="todo-remove" @click="removeTodo( todo.id )">Done</span>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'ToDoList',
  props: {
    todos: Array,
    addTodo: Function,
    removeTodo: Function
  },
  data() {
    return {
      inputText: ''
    };
  }
};
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
  display: grid;
  grid-auto-flow: column;
}

.todo:nth-child(odd) {
  background: #edf0f5;
}

.todo-task {
  justify-self: start;
}

.todo-remove {
  cursor: pointer;
  justify-self: end;
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
  box-shadow: 0px 4px 10px 0px rgba(0, 0, 0, 0.5);
}
</style>
