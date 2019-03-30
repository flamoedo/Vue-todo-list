<template>
  <div id="app">
    <AddTodo v-on:add-todo="addTodo" />
    <Todos v-bind:todos="todos" v-on:del-todo="deleteTodo"/>
  </div>
</template>

<script>
import Todos from '../components/Todo.vue';
import AddTodo from '../components/AddTodo.vue';
import axios from 'axios';


export default {
  name: 'Home',
  components: {
    Todos,
    AddTodo
  },
  methods:{
    deleteTodo(id){
      axios.delete(`http://jsonplaceholder.typicode.com/todos/${id}`)
      .then(res=>this.todos=this.todos.filter(todo=>todo.id!=id))
      .catch(err=>console.log(err));
    },
    addTodo(newTodo){
      const{title, completed} = newTodo;
      axios.post('http://jsonplaceholder.typicode.com/todos',
      {
        title,
        completed
      }).then(res=>this.todos = [...this.todos, res.data])
      .catch(err=>console.log(err));
    },

  },
  data(){
    return{
      todos:[]
    }
  },
  created(){
    console.log("alo alo alo");
    axios.get('http://jsonplaceholder.typicode.com/todos?_limit=10')
    .then(res=>this.todos = res.data)
    .catch(err=>console.log(err));

}

}
</script>

<style>
*{
box-sizing: border-box;
margin:0;
padding: 0;
}

body{
  font-family: Arial, Helvetica, sans-serif;
  line-height: 1.4;
}
.btn{
  display:inline-block;
  border: none;
  background: #555;
  color:#fff;
  padding: 7px 20px;
  cursor: pointer;
}

.btn:hover{
  background: #777
}

</style>
