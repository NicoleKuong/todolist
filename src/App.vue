<!--output on the browser -->
<template>
  <div id="app">
    <Header />
    <!--catch that emit from AddTodo.vue -->
    <AddTodo v-on:add-todo="addTodo" />
    <!-- use template directive v-bind to pass the data into the component (as props) -->
    <Todos v-bind:todos="todos" v-on:del-todo="deleteTodo" />
  </div>
</template>

<!-- need to define what components you are using in the
export default object
-->
<script>
import Header from "./components/layout/Header";
import Todos from "./components/Todos";
import AddTodo from "./components/AddTodo";
import axios from "axios";

export default {
  name: "App",
  components: { Header, Todos, AddTodo },
  //keep the data in the app component so then other components can have access to it (lifting state)
  //data is a function that returns an object
  data() {
    return {
      todos: [],
    };
  },
  methods: {
    deleteTodo(id) {
      axios
        .delete(`https://jsonplaceholder.typicode.com/todos/${id}`)
        //Disable no-unused-vars For Unused Parameter
        /* eslint no-unused-vars: ["error", { "args": "none" }] */
        .then(
          (res) => (this.todos = this.todos.filter((todo) => todo.id !== id))
        )
        .catch((err) => console.log(err));
    },
    addTodo(newTodo) {
      const { title, completed } = newTodo;
      axios
        .post("https://jsonplaceholder.typicode.com/todos", {
          title,
          completed,
        })
        .then((res) => (this.todos = [...this.todos, res.data]))
        .catch((e) => console.log(e));
    },
  },
  //created is like componentDidMount()/useEffect()
  //fetch data from a REST API
  created() {
    axios
      .get("https://jsonplaceholder.typicode.com/todos?_limit=10")
      .then((res) => (this.todos = res.data))
      .catch((e) => console.log(e));
  },
};
</script>

<!-- global -->
<style>
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

body {
  font-family: Arial, Helvetica, sans-serif;
  line-height: 1.4;
}

.btn {
  display: inline-block;
  border: none;
  background: #555;
  color: #fff;
  padding: 7px 20px;
  cursor: pointer;
}
.btn:hover {
  background: #666;
}
</style>
