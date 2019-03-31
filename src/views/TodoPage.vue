<template>
  <div id="app">
    <AddTodo @add-todo="addTodo"/>
    <Todo v-bind:todos="todos" v-on:del-todo="deleteTodo" ></Todo>
  </div>
</template>

<script>
import HelloWorld from '../components/HelloWorld.vue';
import Todo from "../components/Todos.vue";
import Header from "../components/layout/Header";
import AddTodo from "../components/AddTodo";

import axios from "axios";

export default {
  name: 'TodoPage',
  components: {
    HelloWorld,
    Todo,
    Header,
    AddTodo
  },
  data(){
    return {
      msg: "Hello",
      todos:[
        {
          id: 1,
          title:"TODO ONE",
          completed: false
        },
         {
          id: 2,
          title:"TODO TWO",
          completed: true
        },
         {
          id: 3,
          title:"TODO Third",
          completed: false
        }
      ]
    }
  },
  created(){
    // install axios: npm i axios
    axios.get("https://jsonplaceholder.typicode.com/todos")
    .then(res=>{
      this.todos = res.data;
    }).catch(err=>console.log(err));
  },

  methods:{
    deleteTodo(id){
      axios.delete(`https://jsonplaceholder.typicode.com/todos/${id}`)
      .then(res=>this.todos=this.todos.filter(todo=>todo.id!==id))
      .catch(err=>console.log(err));
      //this.todos = this.todos.filter(todo=> todo.id !== id);
    },
    addTodo(newTodo){
      const {title, completed} = newTodo;
      axios.post("https://jsonplaceholder.typicode.com/todos",{
        title,
        completed
      })
      .then(res=>this.todos =[...this.todos,newTodo])
      .catch(err=>console.log(err));

      //this.todos = [...this.todos,newTodo];
    },
    // use 'https://jsonplaceholder.typicode.com/todos/1
    
  }
}
</script>

<style>
*{
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
body{
  font-family: Arial, Helvetica, sans-serif;
  line-height: 1.4;
}
.btn{
  display: inline-block;
  border: none;
  background: #555;
  color: #fff;
  padding: 7px 20px;
  cursor: pointer;
}
.btn:hover{
  background: #666;
}
</style>
