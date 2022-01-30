<template>
  <div id="bg">
    <div id="app">
      <img alt="Vue logo" src="./assets/logo.png" />
      <TodoApp />
    </div>
  </div>
</template>

<script>
import TodoApp from "./components/ToDoApp.vue";

export default {
  name: "App",
  components: {
    TodoApp,
  },
};
</script>

<style>
* {
  margin: 0;
  padding: 0;
  border: 0;
}
#bg {
  background-color: #aaff88;
  min-height: 100vh;
  padding: 60px 0;
  transition: min-height 1s ease;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin: auto;
  padding: 25px 0;
  background-color: #5aff88;
  width: 70%;
  min-height: 75vh;
  border-radius: 20px;
  transition: all 1s ease;
}
</style>
