<template>
  <div class="add-to-do-container">
    <div class="add-to-do-input-container">
      <input class="add-to-do-input" type="text" v-model="todo" />
    </div>
    <div class="add-to-do-icon-container">
      <i class="fa-solid fa-plus fa-2x" @click="addTodo"></i>
    </div>
  </div>
</template>

<script>
export default {
  name: "AddTodo",
  data() {
    return {
      todo: "",
    };
  },
  methods: {
    addTodo() {
      this.$emit("addTodo", {
        id: Math.random(),
        task: this.todo,
        done: false,
      });
      this.todo = "";
    },
  },
};
</script>

<style scoped>
.add-to-do-container {
  display: flex;
  align-items: center;
}
.add-to-do-input-container {
  display: flex;
  align-items: center;
  border: 2px solid grey;
  width: 80%;
  margin-left: 20px;
}
.add-to-do-icon-container {
  background-image: linear-gradient(
    to right,
    #f0dab2,
    #ebd78c,
    #dbd667,
    #c1d741,
    #9ada0b
  );
  padding: 8px;
}
.add-to-do-icon-container :hover {
  cursor: pointer;
}
.add-to-do-input {
  flex: 1;
  height: 40px;
  border: none;
  outline: none;
}
</style>
