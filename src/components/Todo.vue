<template>
  <div>
    <input v-model="newTodoText"
           @keyup.enter="addNewTodo"
           placeholder="Add a todo"
    >
    <ul>
      <li v-for="(todoItem, index) in todos"
          :key="todoItem.id"
          :title="todoItem.title"
          @remove="todos.splice(index, 1)"
      >
        {{todoItem.title}}
        <button v-on:click="$emit('remove')">X</button></li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "Todo",
  data: () => {
    return {
      newTodoText: "",
      title: "",
      todos: [
        {
          id: 1,
          title: "Do the dishes"
        },
        {
          id: 2,
          title: "Take out the trash"
        },
        {
          id: 3,
          title: "Mow the lawn"
        }
      ],
      nextTodoId: 4
    };
  },
  methods: {
    addNewTodo: () => {
      this.todos.push({
        id: this.nextTodoId++,
        title: this.newTodoText
      });
      this.newTodoText = "";
    }
  }
};
</script>
