<template>
  <div>
    <div v-bind:key="todo.id" v-for="todo in todos">
      <!-- bind/pass the todo from above as props into TodoItem -->
      <!-- catch del-todo from app.use-->
      <TodoItem v-bind:todo="todo" v-on:del-todo="$emit('del-todo', todo.id)" />
    </div>
  </div>
</template>

<script>
//import the todoitem component
import TodoItem from "./Todoitem.vue";
export default {
  name: "Todos",
  components: {
    TodoItem
  },
  props: ["todos"]
};
</script>

<style scoped></style>
