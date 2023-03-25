<script>

import App2 from "./App2.vue"

let id = 0;

export default {

  components: {
    App2
  },
  data() {
    return {
      message: 'Hello World!',
      count: 0,
      text: '',
      newTodo: '',
      todos: [
        { id: id++, text: 'Aprende HTML' },
        { id: id++, text: 'Aprende JavaScript' },
        { id: id++, text: 'Aprende Vue' }
      ]
    }
  },
  methods: {
    increment() {
      this.count++
    },
    addTodo(){
      this.todos.push({ id: id++, text: this.newTodo })
      this.newTodo = '';
    },
    removeTodo(todo){
      this.todos = this.todos.filter((t) => t !== todo);
    }
  }
}

</script>


<template>

<h1>{{ message }}</h1>
<h1>{{ message.split('').reverse().join('') }}</h1>
<hr>
<button @click="increment">count is: {{ count }}</button>

<h1 v-if="count>10">El contador es mayor a 10</h1>
<h1 v-else>El contador es menor a 10</h1>
<hr>
<p>Probando input</p>
<input v-model="text" placeholder="Type here">
  <p>Ingresaste: {{ text }}</p>
  
 <br>
 <p> Probando la lista</p> 
   
   <form @submit.prevent="addTodo">
    <input v-model="newTodo">
    <button>Add Todo</button>    
  </form>
  <ul>
    <li v-for="todo in todos" :key="todo.id">
      {{ todo.text }}
      <button @click="removeTodo(todo)">X</button>
    </li>
  </ul>
  <App2></App2>
</template>


<style>

</style>