<template>
  <div id="app">
    <h1 class="title">Todo-List</h1>
    <form>
      <input type="text" placeholder="Add a new todo item" v-model="newTodo" class="form-input dark">
      <button type="submit" @click.prevent="addTodo" class="form-button dark">Add</button>
    </form>
    <ul class="todo-list">
      <li v-for="(todo, index) in todos" :key="index" class="todo-item">
        <div class="todo-text dark">{{ todo }}</div>
        <button @click="deleteTodo(index)" class="delete-button dark">Delete</button>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  data() {
    return {
      newTodo: '',
      todos: [],
    }
  },
  methods: {
    addTodo() {
      if (this.newTodo !== '') {
        this.todos.push(this.newTodo)
        this.newTodo = ''
      }
    },
    deleteTodo(index) {
      this.todos.splice(index, 1)
    },
  },
}
</script>

<style>
   body {
    background-color: #121212;
    color: #fff;
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
    margin: 0;
  }

  #app {
    display: flex;
    flex-direction: column;
    align-items: center;
  }

  .title {
    color: #fff;
    margin-bottom: 20px;
    text-align: center;
    font-family: Arial, Helvetica, sans-serif;
  }

  .form-input, .form-button {
    background-color: #212121;
    border: none;
    color: #fff;
    padding: 10px;
    margin-right: 10px;
    border-radius: 5px;
  }

  .form-input:focus {
    outline: none;
  }

  .todo-list {
    list-style: none;
    padding: 0;
  }

  .todo-item {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-top: 10px;
    padding: 10px;
    background-color: #212121;
    border-radius: 5px;
  }

  .todo-text {
    flex: 1;
    color: #fff;
    margin-right: 10px;
  }

  .delete-button {
    background-color: #f44336;
    border: none;
    color: #fff;
    padding: 5px 10px;
    border-radius: 5px;
    cursor: pointer;
  }

  .delete-button:hover {
    background-color: #d32f2f;
  }
</style>
