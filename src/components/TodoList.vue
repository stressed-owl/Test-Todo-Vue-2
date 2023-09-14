<template>
  <div class="todo-list">
    <todo-item
      v-for="todo in todos"
      :key="todo.id"
      :todo="todo"
    />
  </div>
</template>

<script>
import TodoItem from "./TodoItem.vue";
export default {
  components: { TodoItem },
  name: "todo-list",
  props: {
    todos: Array,
  },
};
</script>

<style scoped>
.todo-list {
  display: flex;
  justify-content: center;
  flex-wrap: wrap;
  gap: 16px;
}
</style>
