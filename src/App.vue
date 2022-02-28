<template>
  <div id="app">

    <div class="container">
    <h3 class="heading">Todo App</h3>
    <input type="text" class="holder" placeholder="Add Task" v-model="value">
    <button @click="adding"> {{isUpdate?"Update":"Add Task"}}</button>
    <ul>
        <todo-app v-for="(item,index) in todoItems" :todo="item" :index="index" :key="item.id" @editTodo="editItem" @deleteTodo="delTodoItem">
        </todo-app>    
    </ul>
  </div>
  </div>
</template>

<script>
import TodoApp from './components/TodoApp.vue'
let id= 0

export default {
  name: 'App',

  components: {
    TodoApp
  },

  data() {
    return {
      value: "",
      todoItems:[],
      index:null,
      isUpdate: false
    }
  },


methods:{
  adding() {
    if(this.value !="" && !this.isUpdate){
      this.todoItems.push({id:id++,text:this.value})
    this.value=""
    }
    else{
      this.todoItems[this.index].text = this.value
      this.isUpdate= false
      this.value = ""
      
    }
  },

  delTodoItem(todo){
    this.todoItems=this.todoItems.filter(t => t != todo)
  },
  editItem(todo,index){
    this.value=todo.text
    this.index = index
    this.isUpdate = true

  }
}  
} 
  
</script>
<style>
.container{
  text-align: center;
}
.holder{
  margin-right: 20px;
}
</style>

