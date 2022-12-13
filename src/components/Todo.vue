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
      <i class="fa-solid fa-pen" @click="toggleModal"></i>
      <i class="fa-solid fa-xmark" @click="$emit('deleteTodo', todo.id)"></i>
    </div>
    <Modal
      @close="toggleModal"
      :modalActive="modalActive"
      @save="$emit('save', { id: todo.id, task: newTodo })"
    >
      <div class="modal-content">
        <h2>Edit todo</h2>
        <div class="edit-todo-input">
          <input type="text" v-model="newTodo" />
        </div>
      </div>
    </Modal>
  </div>
</template>

<script>
import Modal from "./Modal.vue";
import { ref } from "vue";

export default {
  name: "Todo",
  props: {
    todo: Object,
  },
  components: {
    Modal,
  },
  data() {
    return {
      newTodo: this.todo.task,
    };
  },
  setup() {
    const modalActive = ref(false);
    const toggleModal = () => {
      modalActive.value = !modalActive.value;
    };
    return { modalActive, toggleModal };
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
.modal-content {
  display: flex;
  flex-direction: column;
}

h2 {
  margin-bottom: 16px;
}

.edit-todo-input {
  border: 1px solid grey;
  width: 50%;
  margin: 0 auto 16px;
  height: 40px;
  display: flex;
  align-content: center;
  justify-content: center;
}

.edit-todo-input input {
  border: none;
  width: 80%;
  outline: none;
  cursor: text;
}
</style>
