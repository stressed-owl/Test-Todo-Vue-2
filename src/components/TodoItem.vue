<template>
  <div class="todo-item">
    <div class="todo-item-wrapper">
      <div class="todo-item-left-content">
        <p class="todo-item-task">
          <strong>{{ todo.task }}</strong>
        </p>
        <p class="todo-item-desc">
          {{ todo.description }}
        </p>
        <p class="todo-item-completed-status">
          Completed: {{ todo.completed }}
        </p>
      </div>
      <div class="todo-item-right-content">
        <button @click="deleteTodo" class="todo-delete">
          <i class="fa-solid fa-trash"></i>
        </button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "todo-item",
  props: {
    todo: Object,
  },
  methods: {
    deleteTodo() {
      this.$store.commit("deleteTodo", this.todo.id);
    },
  },
};
</script>

<style scoped>
* {
  color: white;
}
.todo-item {
  background-color: #c33c54;
  padding: 16px;
  border-radius: 4px;
  min-width: 240px;
  min-height: 140px;
}

.todo-item-task {
  font-size: 21px;
}

.todo-item-wrapper {
  display: flex;
  align-items: center;
  justify-content: space-between;
  column-gap: 12px;
}

.todo-item-desc {
  margin-top: 10px;
}

.todo-item-completed-status {
  margin-top: 20px;
}

.todo-delete {
  background: transparent;
  border: none;
  outline: none;
  font-size: 24px;
}
</style>
