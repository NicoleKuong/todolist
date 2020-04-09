<!--output on the browser -->
<template>
  <div id="app">
    <!-- use template directive v-bind to pass the data into the component (as props) -->
    <Todos v-bind:todos="todos" />
  </div>
</template>

<!-- need to define what components you are using in the
export default object
-->
<script>
import Todos from "./components/Todos";
export default {
  name: "App",
  components: { Todos },
  //keep the data in the app component so then other components can have access to it (lifting state)
  //data is a function that returns an object
  data() {
    return {
      todos: [
        { id: 1, title: "Todo One", completed: false },
        { id: 2, title: "Todo Two", completed: true },
        { id: 3, title: "Todo Three", completed: false },
      ],
    };
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
</style>
