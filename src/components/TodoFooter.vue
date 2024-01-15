<template>
  <div class="clearAllContainer">
    <span class="clearAllBtn" @click="clearTodo">Clear All</span>
  </div>
</template>

<script>
export default {
  methods : {
    clearTodo() {
      this.$emit("clearAll");
    }
  }

}
</script>

<style scoped>
  .clearAllContainer {
    margin: 0 auto;
    width: 8.5rem;
    height: 50px;
    line-height: 50px;
    background-color: white;
    border-radius: 5px;
  }
  .clearAllBtn {
    display: block;
    cursor: pointer;
    color: #e20303;
  }
</style>