<template>
  <div class="todo">
    <Header />
    <AddTodo v-on:add-todo="addTodo"/>
    <Todos v-bind:todos='todos' v-on:del-todo="deleteTodo"/>
  </div>
</template>

<script>
import Header from '../components/layout/Header';
import Todos from '../components/Todos';
import AddTodo from '../components/AddTodo';
import axios from 'axios';

export default {
  name: 'todo',
  components: {
    Header,
    Todos,
    AddTodo
  },
  data(){
    return {
      todos: []
    }
  },//58:14
  methods: {
    deleteTodo(id){
      axios.delete(`https://jsonplaceholder.typicode.com/todos/${id}`)
        .then( res =>  this.todos = this.todos.filter( todo => todo.id !== id ) )
        .catch( err => console.log(err));

    },
    addTodo(newTodo){
      const { title, completed } = newTodo;
      axios.post('https://jsonplaceholder.typicode.com/todos', {
        title,
        completed
      })
      .then(res => this.todos = [...this.todos, res.data])
      .catch(e => console.log(e))
      this.todos = [...this.todos, newTodo];
    }
  },
  created(){
    axios.get('https://jsonplaceholder.typicode.com/todos?_limit=5')
      .then(res => this.todos = res.data)
      .catch(e => cosole.log(e));
  }
}
</script>

<style scoped>

</style>