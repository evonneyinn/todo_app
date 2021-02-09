<template>
  <ul>
    <todo-item
      v-for="item in todos"
      v-bind:todo="item"
      v-bind:key="item.id"
      v-on:delete-todo="deleteTodo"
    ></todo-item>
    <create-new-todo v-on:new-todo="addTodo"></create-new-todo>
  </ul>
</template>

<script>
import TodoItem from './TodoItem'
import CreateNewTodo from './CreateNewTodo.vue'
export default {
  components: {
    TodoItem,
    CreateNewTodo
  },
  data () {
    return {
      todos: [
      ]
    }
  },
  methods: {
    deleteTodo (todo) {
      const itemIndex = this.todos.indexOf(todo)
      this.todos.splice(itemIndex, 1)
    },
    addTodo (newStr) {
      var newID = 0
      if (this.todos.length !== 0) {
        newID =
          this.todos.reduce((a, b) => (Number(a.id) > Number(b.id) ? a : b)) +
          1
      }

      var newTodo = {
        id: newID,
        text: newStr,
        checked: false
      }
      this.todos.push(newTodo)
    }
  }
}
</script>

<style scoped>
ul {
  list-style-type: none;
  padding: 0;
}
</style>
