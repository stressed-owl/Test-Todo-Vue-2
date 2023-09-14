<template>
  <div>
    <form class="todo-form" @submit.prevent>
      <p>{{ inputValidation }}</p>
      <div class="todo-form-input-wrapper">
        <input
          class="todo-form-input"
          type="text"
          placeholder="Task..."
          v-model="task"
        />
      </div>
      <div class="todo-form-input-wrapper">
        <input
          class="todo-form-input"
          type="text"
          placeholder="Description..."
          v-model="description"
        />
      </div>
      <button class="todo-add" @click="addTodo">Add to-do</button>
    </form>
  </div>
</template>

<script>
export default {
  data() {
    return {
      task: "",
      description: "",
    };
  },
  methods: {
    addTodo() {
      if (this.task.length > 0) {
        const todo = {
          id: Date.now(),
          task: this.task,
          description: this.description,
          completed: false,
        };
        this.$store.commit("addTodo", todo);
        this.task = "";
        this.description = "";
      }
    },
  },
  computed: {
    inputValidation() {
      return this.task.length > 0 ? "" : "'Task' field is required";
    },
  },
};
</script>

<style scoped>
.todo-form {
  display: flex;
  align-items: center;
  flex-direction: column;
  row-gap: 16px;
}

.todo-form-input {
  padding: 12px 16px;
  border-radius: 6px;
  border: none;
  border: 1px solid #c33c54;
  color: #c33c54;
  outline: none;
  max-width: 300px;
  min-width: 240px;
}

::placeholder {
  color: #c33c54;
}

.todo-form-input:focus {
  border: 1px solid #c33c54;
}

.todo-add {
  padding: 12px 16px;
  border: none;
  border-radius: 6px;
  background-color: #c33c54;
  color: #fff;
  font-size: 17px;
  margin-top: 16px;
}

.todo-add:hover {
  transition: 0.3s;
  background-color: #cf6377;
}
</style>
