<!--output on the browser -->
<template>
  <div id="app">
    {{ todos }}
  </div>
</template>

<!-- need to define what components you are using in the
export default object
-->
<script>
export default {
  name: "App",
  components: {},
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
