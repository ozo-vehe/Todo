<template>
  <TodoApp />
</template>

<script>
import TodoApp from './components/TodoApp.vue'

export default {
  name: 'App',
  components: {
    TodoApp
  },
  data() {
    return {
      
    }
  },
  methods: {
    addNewTodo(todo) {
      this.newTodoList.push(todo)
      console.log(this.newTodoList)
    }
  },
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Lato&display=swap');
@import url('https://fonts.googleapis.com/css2?family=Spartan&display=swap');

body {
  padding: 0px;
  margin: 0px;
}
#app {
  font-family: 'Spartan';
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c2a2a;
  font-size: 16px;
  background-color: #fafcf9;
}
</style>
