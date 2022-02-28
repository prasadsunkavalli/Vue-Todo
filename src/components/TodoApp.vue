<template>

   <div class="boxed">
  <input type="checkbox" @click="boxClicked" class="checkBox"/>
  <p :class="{marked: isChecked}">{{todo.text}}</p>
  <button @click="$emit('editTodo',todo,index)">Edit</button>
  <button @click="$emit('deleteTodo',todo)">Delete</button>
   </div>
  

</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    todo: Object,
    index: Number
  },
data() {
    return {
      isChecked:false,

    }
  },
methods:{
  boxClicked() {
    this.isChecked=!this.isChecked
    }
}


}
</script>
<style>
.marked{
  text-decoration: line-through;
}
.boxed{
  width:100%;
  display: flex;
  flex-direction: row;
  justify-content: center;
  align-items: center;
  text-align: center;
}
.delButton{
  width: 50px;
  height: 20px;
  margin-left: 20px;
}
.checkBox{
  margin-right: 20px;
}
</style>

