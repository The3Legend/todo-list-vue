<template>
  <div id="app">
    <TodoList />
    <InputWrite />
  </div>
</template>

<script>
import "bootstrap/dist/css/bootstrap.css";
import "bootstrap-vue/dist/bootstrap-vue.css";
import InputWrite from "@/components/InputWrite";
import TodoList from "@/components/TodoList";

export default {
  name: "App",
  components: {
    InputWrite,
    TodoList,
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
</style>
