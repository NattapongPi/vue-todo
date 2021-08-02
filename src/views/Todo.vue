<template>
  <div class="todo-page">
    <h1>Todo page</h1>
    <form @submit.prevent="handleSubmit">
      <input v-model.lazy="newTodo" placeholder="Type something..." />
      <button type="submit">Submit</button>
    </form>
    <TodoList :todos="todos" />
  </div>
</template>

<script>
import TodoList from "../components/TodoList.vue";

export default {
  components: {
    TodoList,
  },
  data() {
    return {
      newTodo: "",
      todos: [],
      nextTodoId: 0,
    };
  },
  methods: {
    handleSubmit() {
      if (!this.newTodo) return;
      this.todos.push({
        id: this.nextTodoId++,
        title: this.newTodo,
      });
      this.newTodo = "";
    },
  },
};
</script>

<style>
.todo-page {
  width: 100%;
  display: flex;
  padding-top: 160px;
  flex-direction: column;
  align-items: center;
}
</style>
