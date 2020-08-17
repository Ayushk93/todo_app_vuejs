<template>
  <div> 
    <TodoList />
  </div>
</template>

<script> 
import TodoList from './components/TodoList'
export default {
  name: 'App',
  components: {
    TodoList
  }
}
</script>

<style> 

body{
  background-color: lightcyan;
  color:black;
}

</style>