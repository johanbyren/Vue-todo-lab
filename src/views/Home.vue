<template>
  <div id="app">
    <AddFunnyPic />
    <AddTodo v-on:add-todo="addTodo" />
    <Todos v-bind:todos="todos" v-on:del-todo="deleteTodo" />
  </div>
</template>

<script lang="ts">
import Vue from "vue";
import Todos from "../components/Todos.vue";
import AddTodo from "../components/AddTodo.vue";
import AddFunnyPic from "../components/AddFunnyPic.vue";
import axios from "axios";

export default Vue.extend({
  name: "Home",
  components: {
    Todos,
    AddTodo,
    AddFunnyPic
  },
  data() {
    return {
      todos: [] as any[]
    };
  },
  methods: {
    deleteTodo(id: number) {
      axios
        .delete(`https://jsonplaceholder.typicode.com/todos/${id}`)
        .then(res => (this.todos = this.todos.filter(todo => todo.id !== id)))
        .catch(err => console.log("Error: ", err));
    },
    addTodo(newTodo: any) {
      const { title, completed } = newTodo;
      axios
        .post("https://jsonplaceholder.typicode.com/todos", {
          title,
          completed
        })
        .then(res => (this.todos = [...this.todos, res.data]))
        .catch(err => console.log("Error: ", err));
    }
  },
  created() {
    axios
      .get("https://jsonplaceholder.typicode.com/todos?_limit=5")
      .then(res => (this.todos = res.data))
      .catch(err => console.log(err));
  }
});
</script>

<style lang="scss">
.btn {
  display: inline-block;
  border: none;
  background: #555;
  color: #fff;
  padding: 7px 20px;
  cursor: pointer;
}

.btn:hover {
  background: #666;
}
</style>
