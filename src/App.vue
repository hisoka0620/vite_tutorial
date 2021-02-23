<template>
  <div :style="baseStyles">To Do List</div>
  <form @submit.prevent="addNewTodo" :style="form">
    <input type="text" v-model="newTodoText" id="new-todo" placeholder="ここに入力して下さい" :style="input">
    <button :style="button">追加</button>
  </form>
  <ul :style="{display: 'inline-block'}">
    <todoItem 
      v-for="(todo,index) in todos" 
      :key="todo.id"
      :title="todo.title"
      @remove="todos.splice(index, 1)" >
    </todoItem>
  </ul>

</template>

<script>
import todoItem from './components/todoItem.vue'

export default {
  name: 'App',
  components: {
    todoItem
  },
  data() {
  return {
    baseStyles: {
      color: 'pink',
      fontSize: '40px',
      display: 'inline-block'
    },
    newTodoText: '',
    todos: [],
    nextTodoId: 0,
    form: {
      margin: '10px 0'
    },
    input:{
      padding: '8px 10px',
      border: '1px solid pink',
      outline: 'none'
    },
    button:{
      marginLeft: '5px',
      color: 'white',
      backgroundColor: 'pink',
      border: '1px solid white',
      outline: 'none',
      padding: '6px 10px',
      cursor: 'pointer'
    }
  }
},
methods: {
    addNewTodo(){
      this.todos.push({
        id: this.nextTodoId++,
        title: this.newTodoText
      })
      this.newTodoText = ''
  }
}
}
</script>
