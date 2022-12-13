<template>
  <button @click="$emit('removeChecked')">
    Remove checked
    <span>
      <i class="fa-solid fa-xmark"></i>
    </span>
  </button>
</template>

<script>
export default {
  name: "RemoveChecked",
};
</script>

<style scoped>
button {
  background-image: linear-gradient(
    to right,
    #f0dab2,
    #ebd78c,
    #dbd667,
    #c1d741,
    #9ada0b
  );
  background-repeat: repeat-y;
  border: 1px solid grey;
  padding: 0 20px;
  font-family: "Josefin Sans";
}
button:hover {
  cursor: pointer;
}
button span {
  margin-left: 5px;
}
</style>
