<template lang="pug">
  div
    header.header
      todo-heading
      todo-input(@addTodo="addTodo")
      todo-list(
        v-if="todos.length > 0",
        :todos="todos",
        @removeTodo="removeTodo",
        @checkTodo="checkTodo",
        @filterTodos="filterTodos"
      )
    pre {{todos}}

</template>

<script>
import todoInput from "./todoInput";
import todoList from "./todoList";
import todoHeading from "./todoHeading";

export default {
  data() {
    return {
      todos: [],
      filter: "all",
    };
  },
  components: {
    todoInput,
    todoList,
    todoHeading,
  },
  methods: {
    addTodo(todo) {
      this.todos.push(todo);
    },
    removeTodo(todoId) {
      this.todos = this.todos.filter((item) => item.id !== todoId);
    },
    checkTodo(todo) {
      this.todos = this.todos.map((item) =>
        item.id === todo.id ? todo : item
      );
    },
    filterTodos(filter) {
      this.filter = filter;
    },
  },
};
</script>
