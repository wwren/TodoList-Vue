<template>
  <div
    class="done-summary-container"
    :style="{ 'background-size': completedTaskPercentage }"
  >
    <p>{{ completedTask }} of {{ totalTask }} done</p>
  </div>
</template>

<script>
export default {
  name: "DoneSummary",
  props: {
    completedTask: Number,
    totalTask: Number,
    completedTaskPercentage: String,
  },
};
</script>

<style scoped>
.done-summary-container {
  border: 1px solid grey;
  width: 40%;
  height: 40px;
  display: flex;
  align-items: center;
  justify-content: center;
  background-image: linear-gradient(
    to right,
    #f0dab2,
    #ebd78c,
    #dbd667,
    #c1d741,
    #9ada0b
  );
  background-repeat: repeat-y;
  transition: background-size 2s ease-in;
}
</style>
