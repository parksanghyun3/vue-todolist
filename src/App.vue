<template>
  <div id="app">
    <div class="todo-wrap">
      <TodoHeader></TodoHeader>
      <TodoInput @addTodoItem="addTodoItem"></TodoInput>
      <TodoList @toggleItem="toggleItem"  @removeTodo="removeTodo" :propsdata="todoItems"></TodoList>
      <TodoFooter @clearAll="clearAllItems"></TodoFooter>
    </div>
  </div>
</template>

<script>
import TodoHeader from './components/TodoHeader.vue'
import TodoInput from './components/TodoInput.vue'
import TodoList from './components/TodoList.vue'
import TodoFooter from './components/TodoFooter.vue'
export default {
  data() {
    return {
      todoItems: []
    }
  },
  components : {
    TodoHeader,
    TodoInput,
    TodoList,
    TodoFooter
  },
  created(){
    for(var i = 0 ; i < localStorage.length ; i++){
      if(localStorage.key(i) !== 'loglevel:webpack-dev-server'){
        this.todoItems.push(JSON.parse(localStorage.getItem(localStorage.key(i))))
      }
    }
  },
  methods: {
    addTodoItem(newTodoItem) {
      let obj = {
        item : newTodoItem,
        status : false,
      }
      localStorage.setItem(newTodoItem, JSON.stringify(obj));
      this.todoItems.push(obj)
    },
    removeTodo(todoItem, index){
      localStorage.removeItem(todoItem.item)
      this.todoItems.splice(index, 1)
      console.log("삭제");
    },
    clearAllItems(){
      localStorage.clear();
      this.todoItems = [];
      console.log("모두삭제")
    },
    toggleItem(todoItem, index){
      this.todoItems[index].status = !this.todoItems[index].status;
      localStorage.removeItem(todoItem.item);
      localStorage.setItem(todoItem.item, JSON.stringify(todoItem))
    }
  }
}
</script>

<style>
  body {
    display: flex;
    justify-content: center;
    align-items: center;
    width: 100%;
    height: 100vh;
    background-color : #f6f6f6;
  }
  .todo-wrap {
    width: 600px;
    text-align: center;
  }
  input {
    padding: 0 20px;
    width: 100%;
    height: 50px;
    line-height: 50px;
    border-radius: 5px;
    box-sizing: border-box;
  }
  .shadow {
    box-shadow: 5px 10px 10px rgba(0,0,0,0.03);
  }
</style>