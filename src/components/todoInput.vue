<template lang="pug">
  .todo-input
    input.input(
      type="text",
      placeholder="What needs to be done?",
      autofocus,
      v-model="todo.name",
      @keydown.enter="addTodo"
    )
</template>
<script>
let uniqId = 0;
export default {
  data() {
    return {
      todo: {
        id: 0,
        name: "",
        checked: false,
      },
    };
  },
  methods: {
    addTodo() {
      uniqId++;
      this.todo.id = uniqId;
      this.$emit("addTodo", {...this.todo});
      this.todo.name = "";
    },
  },
};
</script>
<style lang="postcss" scoped>
.input {
  font-size: 24px;
  padding: 16px 16px 16px 60px;
  border: none;
  background: rgba(0, 0, 0, 0.003);
  box-shadow: inset 0 -2px 1px rgba(0, 0, 0, 0.03);
  line-height: 1.4em;
  outline: none;
  color: inherit;
  width: 100%;
  background: #fff;
}
</style>
