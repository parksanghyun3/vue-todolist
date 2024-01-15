<template>
  <ul>
    <li v-for="(todoItem, index) in propsdata" :key="todoItem.item">
        <span @click="toggleComplete(todoItem, index)">
          <i class="check-btn fas fa-check" :class="{checkBtnCompleted: todoItem.status}"></i>
        </span>
        <span :class="{textCompleted: todoItem.status}">{{todoItem.item}} </span>
        <span class="remove-btn" @click="removeTodo(todoItem, index)">
          <i class="fas fa-trash-alt"></i>
        </span>
    </li>
  </ul>
</template>

<script>
export default {
    props: ["propsdata"],
    methods: {
      removeTodo(todoItem, index) {
        this.$emit("removeTodo", todoItem, index);
      },
      toggleComplete(todoItem, index) {
        this.$emit("toggleItem", todoItem, index);
        console.log(todoItem, index)
      },
    }

}
</script>

<style scoped>
ul {
  list-style-type: none;
  padding-left: 0px;
  margin-top: 0;
  text-align: left;
}
li {
  display: flex;
  min-height: 50;
  height: 50px;
  line-height : 50px;
  margin: 0.5rem 0;
  padding: 0 0.9rem;
  background: white;
  border-radius: 5px;
}
.check-btn {
  line-height: 45px;
  color: #62acde;
  margin-right: 5px;
}
.remove-btn {
  cursor: pointer;
  margin-left: auto;
  color : #de4343;
}
.checkBtnCompleted {
color : #b3adad;
}
.textCompleted {
  text-decoration: line-through;
  color: #b3adad;
}
</style>