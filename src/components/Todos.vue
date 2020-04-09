<template>
  <div>
    <div v-bind:key="todo.id" v-for="todo in todos">
      <!-- bind/pass the todo from above as props into TodoItem -->
      <TodoItem v-bind:todo="todo" />
    </div>
  </div>
</template>

<script>
//import the todoitem component
import TodoItem from "./Todoitem";
export default {
  name: "Todos",
  components: {
    TodoItem,
  },
  props: ["todos"],
};
</script>

<style scoped></style>
