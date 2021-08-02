<template>
  <div class="todo-list">
    <div class="todo-title" v-for="(todo, index) in todos" :key="todo">
      {{ todo.title }}
      <button @click="del(index)">delete</button>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    todos: Array,
  },
  methods: {
    del(index) {
      this.todos.splice(index, 1);
    },
  },
};
</script>

<style>
.todo-list {
  width: 50vw;
  padding-top: 10px;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}

.todo-title {
  width: 100%;
  padding: 10px 20px;
  border: 1px solid #eeeeee;
  transition: 0.2s;
  cursor: pointer;
  display: flex;
  justify-content: space-between;
  align-items: center;
  box-sizing: border-box;
  position: relative;
}

.todo-title:hover {
  border: 1px solid #c4c4c4;
}
</style>
