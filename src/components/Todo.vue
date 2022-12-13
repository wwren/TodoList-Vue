<template>
  <div class="todo-container">
    <div class="todo-item">
      <input
        type="checkbox"
        :id="todo.id"
        :name="todo.id"
        :checked="todo.done"
        @change="$emit('toggleDone', todo.id)"
      />
      <p :class="{ done: todo.done }">{{ todo.task }}</p>
    </div>
    <div class="todo-tool">
      <i class="fa-solid fa-pen" @click="$emit('editTodo', todo.id)"></i>
      <i class="fa-solid fa-xmark" @click="$emit('deleteTodo', todo.id)"></i>
    </div>
  </div>
</template>

<script>
export default {
  name: "Todo",
  // data() {
  //   return {
  //     check: false,
  //   };
  // },
  props: {
    todo: Object,
    // checked: Boolean,
  },
};
</script>

<style scoped>
.done {
  text-decoration: line-through;
}
.todo-container {
  display: flex;
  align-items: center;
  justify-content: space-between;
}

input:hover {
  cursor: pointer;
}
.todo-item {
  display: flex;
  align-content: center;
  justify-content: center;
  gap: 10px;
}

.todo-tool {
  display: flex;
  justify-content: space-around;
  gap: 10px;
}
.todo-tool i {
  cursor: pointer;
}
</style>
