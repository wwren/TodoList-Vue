<template>
  <div class="todo-list-container">
    <h1>To do list</h1>
    <AddTodo @addTodo="addTodo" />
    <Todos
      :todos="todos"
      @toggleDone="toggleDone"
      @deleteTodo="deleteTodo"
      @save="save"
    />
    <div class="todo-list-bottom">
      <DoneSummary
        :completedTask="completedTask"
        :totalTask="totalTask"
        :completedTaskPercentage="completedTaskPercentage"
      />
      <RemoveChecked @removeChecked="removeChecked" />
    </div>
  </div>
</template>

<script>
import Todos from "./components/Todos.vue";
import AddTodo from "./components/AddTodo.vue";
import DoneSummary from "./components/DoneSummary.vue";
import RemoveChecked from "./components/RemoveChecked.vue";
export default {
  name: "App",
  components: {
    Todos,
    AddTodo,
    DoneSummary,
    RemoveChecked,
  },
  data() {
    return {
      todos: [],
    };
  },
  methods: {
    toggleDone(id) {
      this.todos = this.todos.map((todo) =>
        todo.id !== id ? todo : { ...todo, done: !todo.done }
      );
    },
    deleteTodo(id) {
      this.todos = this.todos.filter((todo) => todo.id !== id);
    },
    addTodo(todo) {
      this.todos.push(todo);
    },
    removeChecked() {
      this.todos = this.todos.map((todo) => ({ ...todo, done: false }));
    },
    save(newTodo) {
      this.todos = this.todos.map((todo) =>
        todo.id !== newTodo.id ? todo : { ...todo, task: newTodo.task }
      );
    },
  },
  computed: {
    completedTask() {
      return this.todos.filter((todo) => todo.done === true).length;
    },
    totalTask() {
      return this.todos.length;
    },
    completedTaskPercentage() {
      return (
        (this.todos.filter((todo) => todo.done === true).length /
          this.todos.length) *
          100 +
        "%"
      );
    },
  },
  created() {
    this.todos = [
      { id: 1, task: "Study Vue", done: false },
      {
        id: 2,
        task: "Build an app around Vue",
        done: false,
      },
      {
        id: 3,
        task: "Write learning blog",
        done: false,
      },
    ];
  },
};
</script>

<style>
.todo-list-container {
  text-align: center;
  width: 95%;
  margin-left: auto;
  margin-right: auto;
  background-color: white;
  padding: 20px 0;
}

body {
  background-image: linear-gradient(
    to right,
    #f0dab2,
    #ebd78c,
    #dbd667,
    #c1d741,
    #9ada0b
  );
  height: 100vh;
  overflow: hidden;
  font-family: "Josefin Sans";
}

.todo-list-bottom {
  display: flex;
  justify-content: space-between;
  padding: 0 10px;
}

@media (min-width: 821px) {
  .todo-list-container {
    width: 50%;
  }

  .todo-list-bottom {
    padding: 0 20px;
  }
}
</style>
