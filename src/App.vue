<template>
  <div id="app">
    <p>{{text}}</p>
    <!-- <haha :nana="shabi" v-bind="todo"></haha> -->
    <todo></todo>
  </div>
</template>

<script>
import HelloWorld from "./components/HelloWorld";
import Haha from "./components/Haha";
import Todo from "./components/Todo";

export default {
  name: "App",
  components: {
    HelloWorld,
    Haha,
    Todo
  },
  data: () => {
    return {
      text: "你好"
    };
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
