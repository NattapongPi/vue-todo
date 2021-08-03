<template>
  <div class="todo-page">
    <form class="todo-form" @submit.prevent="handleSubmit">
      <input
        class="todo-input"
        v-model.lazy="newTodo"
        placeholder="Type something..."
      />
      <Button>Add</Button>
    </form>
    <TodoList :todos="todos" />
  </div>
</template>

<script>
import TodoList from "../components/TodoList.vue";
import Button from "../components/Button.vue";

export default {
  components: {
    TodoList,
    Button,
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
        id: this.nextTodoId,
        title: this.newTodo,
        isFinish: false,
      });
      this.newTodo = "";
      this.nextTodoId++;
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
.todo-form {
  display: flex;
}
.todo-input {
  width: 100%;
  height: 40px;
  padding: 12px 20px;
  margin-right: 5px;
  box-sizing: border-box;
  border: 3px solid #ccc;
  -webkit-transition: 0.5s;
  transition: 0.5s;
  outline: none;
}
.todo-input:focus {
  border: 3px solid #555;
}
</style>
