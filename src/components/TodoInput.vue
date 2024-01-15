<template>
  <div class="input-box shadow">
    <input type="text" v-model="newTodoItem" @keypress.enter="addTodo">
    <span class="add-container" @click="addTodo">
        <i class="fas fa-plus addBtn"></i>
    </span>
  </div>
</template>

<script>
export default {
  data() {
    return {
      newTodoItem : ""
    }
  },
  methods: {
    addTodo(){
      if(this.newTodoItem !== ""){
        let value = this.newTodoItem && this.newTodoItem.trim();
        this.$emit("addTodoItem", value);
        this.clearInputbox();
      }
    },
    clearInputbox(){
      this.newTodoItem = "";
    }
  }
}
</script>

<style scoped>
input:focus {
  outline: none;
}
.input-box {
  display: flex;
  align-items: center;
  background: white;
  border-radius: 5px;
}
.input-box input {
  border-style: none;
  font-size: 0.9rem;
}
.add-container {
  display: block;
  height: 50px;
  line-height: 50px;
  background: linear-gradient(to right, #6478FB, #8763FB);
  width: 3rem;
  border-radius: 0 5px 5px 0;
}
.addBtn {
  cursor: pointer;
  color: white;
  vertical-align: middle;
}
.closeModalBtn {
  color: #42b983;
}
</style>
