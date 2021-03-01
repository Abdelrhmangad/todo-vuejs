<template>
  <div>
    <TodoList />
  </div>
</template>

<script>
import TodoList from "./components/list.component";
export default {
  name: "App",
  components: {
    TodoList,
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
h1,
h2 {
  text-align: center;
}
</style>
