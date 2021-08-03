<template>
  <div class="todo-list">
    <div class="todo-text">Todo List</div>
    <div
      class="todo-title"
      v-for="(todo, index) in todos"
      :key="todo.id"
      :data-value="todo.id"
    >
      <div
        class="todo-box"
        :class="todo.isFinished && 'isFinished'"
        @click="toggle(index)"
        v-bind:style="[
          todos[index].isFinished
            ? { 'text-decoration': 'line-through', color: 'grey' }
            : { 'text-decoration': 'none', color: 'black' },
        ]"
      >
        {{ todo.title }}
      </div>
      <button class="del-button" @click="del(index)">Delete</button>
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

    toggle(index) {
      this.todos[index].isFinished = !this.todos[index].isFinished;
    },
  },
};
</script>

<style>
.todo-list {
  width: 100%;
  max-width: 1200px;
  padding-top: 10px;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}

.todo-title {
  width: 100%;
  max-width: 500px;
  height: 50px;
  padding-right: 10px;
  border: 1px solid #eeeeee;
  transition: 0.3s;
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

.todo-title.isFinished {
  color: black;
}

.todo-text {
  font-size: 36px;
  padding-top: 30px;
}

.todo-box {
  display: flex;
  padding-left: 10px;
  align-items: center;
  width: 100%;
  height: 100%;
}

.todo-box.isFinished:before {
  color: #c4c4c4;
  content: "";
  position: absolute;
  width: 80%;
  height: 2px;
  background: #9b9b9b;
}

.del-button {
  background-color: white;
  color: red;
  border: 2px solid red;
  transition-duration: 0.4s;
}

.del-button:hover {
  background-color: red;
  color: white;
}
</style>
