<template>
  <div>
    <!-- <p>Completed Tasks: {{todos.filter(todo => {return todo.done === true}).length}}</p>
    ###<p>Pending Tasks: {{todos.filter(todo => {return todo.done === false}).length}}</p>
    -->
    <div></div>
    <todo v-on:delete-todo="deleteTodo"
          v-on:complete-todo="completeTodo"
          :key="todo.title"
          v-bind:todo="todo"
          v-for="todo in todos"
          >
    </todo>
  </div>
</template>

<script type = "text/javascript" >

import Todo from './Todo';
import CreateTodo from './CreateTodo';

export default {
  props: ['todos'],
  components: {
    Todo,
    CreateTodo,
  },
  methods: {
    deleteTodo(todo) {
      const todoIndex = this.todos.indexOf(todo);
      this.todos.splice(todoIndex, 1);
    },
    completeTodo(todo) {
      const todoIndex = this.todos.indexOf(todo);
      this.todos[todoIndex].done = true;
    },
  },
};
</script>
