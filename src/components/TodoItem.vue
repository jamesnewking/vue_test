<template>
  <div class='todo-item' v-bind:class="{'is-complete':todo.completed}">
      <p>
          <input type="checkbox" v-on:change="markComplete" v-bind:checked="todo.completed"> 
          <em class='todoTitle'>{{todo.title}}</em>
          <button @click="$emit('del-todo', todo.id)" class="del">x</button>
          </p>
  </div>
</template>

<script>
export default {
    name: "TodoItem",
    props: ["todo"],
    methods: {
        markComplete() {
            this.todo.completed = !this.todo.completed;
        }
    }
}
</script>

<style scoped>
    .todo-item {
        background: white;
        padding: 10px;
        border-bottom: 1px #ccc dotted;
        text-align: left;
    }
    .is-complete {
        text-decoration: line-through;
    }
    .todoTitle {
        padding-left: 10px;
    }
    .del {
        background: red;
        color: white;
        border: none;
        padding: 3px 8px 4px 8px;
        border-radius: 50%;
        cursor: pointer;
        float: right;
    }
</style>