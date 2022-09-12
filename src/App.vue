<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png" />
    <h2 class="text-centre p-4">Todos app</h2>
    <ul id="example-1" class="list-group">
      <input
        v-model="newTodo"
        type="text"
        name="todo"
        class="m-4 form-control"
        placeholder="Add a new to do"
      />
      <button @click="addTodo()" class="btn btn-info mb-3 form-control">
        Add new to-do
      </button>

      <li
        class="list-group-item list-group-item-info"
        v-for="(item, index) in todos"
        v-bind:key="item.id"
      >
        {{ item.name }}
      </li>
      {{
        newTodo
      }}
      <button @click="deleteTodo(index)" class="btn btn-info mb-3 form-control">
        Delete
      </button>
    </ul>
  </div>
</template>

<script>
export default {
  data() {
    return {
      newTodo: "",
      todos: [
        {
          id: 1,
          name: "Buy a coffee",
        },
        {
          id: 2,
          name: "Make a coffee",
        },
        {
          id: 3,
          name: "Take a coffee",
        },
      ],
    };
  },
  methods: {
    addTodo() {
      const newTodo = {
        id: this.todos[this.todos.length - 1].id + 1,
        name: this.newTodo,
      };
      const todos = this.todos;
      todos.push(newTodo);
      this.newTodo = "";
    },
  },
  deleteTodo(index) {
    this.todos.splice(index, 1);
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
@import "~bootstrap/dist/css/bootstrap.css";
</style>
