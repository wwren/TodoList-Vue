<template>
  <ul>
    <li v-for="todo of todos" v-bind:key="todo.id">
      <Todo
        :todo="todo"
        @toggleDone="$emit('toggleDone', todo.id)"
        @deleteTodo="$emit('deleteTodo', todo.id)"
        @save="(payload) => $emit('save', payload)"
      />
    </li>
  </ul>
</template>

<script>
import Todo from "./Todo.vue";

export default {
  name: "Todos",
  props: {
    todos: Array,
  },
  components: {
    Todo,
  },
  emits: ["toggleDone", "save"],
};
</script>

<style scoped>
ul {
  list-style-type: none;
  padding: 0 20px;
}

ul li {
  border-top: 0.5px solid grey;
}

ul li:last-child {
  border-bottom: 0.5px solid grey;
}
</style>
