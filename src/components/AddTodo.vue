<template>
  <div>
    <form @submit="addTodo">
      <!-- v-model bound the title input with data's title -->
      <input
        type="text"
        v-model="title"
        name="title"
        placeholder="Add Todo..."
      />
      <input type="submit" value="Submit" class="btn" />
    </form>
  </div>
</template>

<script>
import uuid from "uuid";
export default {
  name: "AddTodo",
  data() {
    return {
      title: "",
    };
  },
  methods: {
    addTodo(event) {
      event.preventDefault();
      const newTodo = {
        id: uuid.v4(),
        title: this.title,
        completed: false,
      };
      //send up to parent
      this.$emit("add-todo", newTodo);
      //clear the form
      this.title = "";
    },
  },
};
</script>

<style scoped>
form {
  display: flex;
}
input[type="text"] {
  flex: 10;
  padding: 5px;
}
input[type="submit"] {
  flex: 2;
}
</style>
