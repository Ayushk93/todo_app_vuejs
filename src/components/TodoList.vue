<template>
  <div class="container">
    <div class="row">
      <div class="col-12">
        <p class="display-3">ToDo App</p>
      </div>
    </div>
    <div class="row">
      <AddTodo @on-addtodo="addTodo($event)"/>
    </div>
    <br>
    <div class="row">
      <div class="col-12 col-lg-6">
        
        <ul class="list-group">
          <Todo v-for="(todo, index) in todos" :key="index" 
          :todoString="todo.todoString"
          :completed="todo.completed"
          @on-delete="deleteTodo(todo)"
          @on-toggle="toggleTodo(todo)"
          @on-edit="editTodo(todo, $event)"
          />
        </ul>
      </div>
    </div>
  </div>
</template>

<script>
import Todo from './Todos'
import AddTodo from './NewTodo'
export default {
  components: {
    Todo,
    AddTodo
  },
  data() {
    return {
      todos: [
        { todoString: "Learn Angular", completed: false },
        { todoString: "Learn React", completed: true },
        { todoString: "Learn Vue", completed: false },
        { todoString: "Learn Ionic", completed: true },
      ],
    };
  },
  methods: {
    addTodo(newTodo) {
      this.todos.push({
        todoString: newTodo,
        completed: false,
      });
    },
    toggleTodo(todo) {
      todo.completed = !todo.completed;
    },
    editTodo(todo, newTodoString) {
      todo.todoString = newTodoString;
    },
    deleteTodo(deleteTodo) {
      this.todos = this.todos.filter((todo) => todo !== deleteTodo);
    },
  },
};
</script>

<style>
</style>