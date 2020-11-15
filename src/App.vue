<template>
  <div id="app">
    <div class="flex">
      <h1>Todo app</h1>
      <Count :todos="todos"></Count>
    </div>
    <AddTodo @add-item="addItem" :todos="todos" :clearAll="clearAll" />
    <TodoList :todos="todos" @delete-todo="deleteTodo" />
  </div>
</template>

<script>
import TodoList from "@/components/TodoList";
import AddTodo from "@/components/AddTodo";
import Count from "@/components/Count";
export default {
  name: "App",
  data() {
    return {
      todos: [],
    };
  },
  components: {
    TodoList,
    AddTodo,
    Count,
  },
  mounted() {
    if (localStorage.getItem("todos"))
      this.todos = JSON.parse(localStorage.getItem("todos"));
  },
  watch: {
    todos: {
      handler() {
        console.log("Todo Items array changed!");
        localStorage.setItem("todos", JSON.stringify(this.todos));
      },
      deep: true,
    },
  },
  methods: {
    deleteTodo(id) {
      this.todos = this.todos.filter((t) => t.id !== id);
    },
    addItem(newTodo) {
      this.todos.push(newTodo);
    },
    clearAll() {
      this.todos = [];
    },
  },
};
</script>

<style>
body{
  background: rgb(61,76,78);
  background: linear-gradient(90deg, rgba(61,76,78,1) 0%, rgba(43,112,112,1) 10%, rgba(23,222,186,1) 48%, rgba(0,212,255,1) 100%);
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  max-width: 440px;
  margin: 40px auto;
  background: white;
  padding:20px;
  border-radius:20px;
}
* {
  box-sizing: border-box;
}
.flex {
  display: flex;
  justify-content: space-between;
  align-items: center;
}
@media screen and (max-width: 780px) {
  h1 {
    font-size: 25px;
  }
}
@media screen and (max-width: 420px) {
  h1 {
    font-size: 20px;
  }
}
</style>
