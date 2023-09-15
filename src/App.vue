<template>
  <div class="app">
    <div class="app-wrapper">
      <todo-form />
      <todo-list :todos="todos" />
    </div>
  </div>
</template>

<script>
import { mapState } from "vuex";
import TodoForm from "./components/TodoForm.vue";
import TodoList from "./components/TodoList.vue";
export default {
  components: { TodoList, TodoForm },
  name: "App",
  computed: mapState({
    todos: (state) => state.todos,
  }),
};
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: "Montserrat", sans-serif;
}

.app {
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 16px;
}

.app-wrapper {
  display: flex;
  flex-direction: column;
  row-gap: 40px;
}
</style>
