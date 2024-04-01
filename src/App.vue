<template>
<div id="app">
  <div class="section">
    <div class="container">
      <!-- as a props we are sending todos from here to todos comp -->
      <Todos v-bind:todos="todos" @addTodo="addTodo" @onComplete="complete" @onDelete="deleteTodo"/>   
    </div>
  </div>
</div>
</template>

<script>
import "bulma/css/bulma.css";
import Todos from './components/Todos.vue';
export default {
  name: 'App',
  components: {
    Todos,
  },
  data(){
    return{
      todos: [
      {
    "userId": 1,
    "id": 1,
    "title": "delectus aut autem",
    "completed": true
  },
  {
    "userId": 1,
    "id": 2,
    "title": "quis ut nam facilis et officia qui",
    "completed": false
  },
  {
    "userId": 1,
    "id": 3,
    "title": "fugiat veniam minus",
    "completed": false
  },
  {
    "userId": 1,
    "id": 4,
    "title": "et porro tempora",
    "completed": true
  },
  {
    "userId": 1,
    "id": 5,
    "title": "laboriosam mollitia et enim quasi adipisci quia provident illum",
    "completed": false
  },
  {
    "userId": 1,
    "id": 6,
    "title": "qui ullam ratione quibusdam voluptatem quia omnis",
    "completed": false
  },
      ]
    }
  },
  methods: {
    addTodo(todo){
      this.todos.unshift(todo)
    },
    complete(id){
      const updated_todos= this.todos.map(todo => 
      todo.id == id ? Object.assign(todo, {completed: true}): todo
      );
       this.todo = updated_todos;
    },
    deleteTodo(id){
      let deleted_todos= this.todos.filter(todo=> todo.id != id);
      this.todos= deleted_todos
    },

  },


}
</script>

<style>
#app {
background-color: #f8961e;
font-family: "Roboto";
min-height: 100vh;
}
</style>
