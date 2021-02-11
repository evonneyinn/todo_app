<template>
  <v-col>
    <v-card class="ma-4" elevation="2" outlined style="padding-bottom: 2em">
      <v-app-bar flat color="rgba(0, 0, 0, 0)">
        <v-toolbar-title class="title black--text pl-0">
          {{ title }}
        </v-toolbar-title>
        <v-btn color="grey" icon v-on:click="deleteList(id)">
          <v-icon>mdi-delete</v-icon>
        </v-btn>
      </v-app-bar>
      <ul>
        <todo-item v-for="item in todos" v-bind:todo="item" v-bind:key="item.id" v-on:delete-todo="deleteTodo" style="margin-bottom: 1em"></todo-item>
        <create-new-todo v-on:new-todo="addTodo"></create-new-todo>
      </ul>
    </v-card>
  </v-col>
</template>

<script>
import TodoItem from './TodoItem'
import CreateNewTodo from './CreateNewTodo.vue'

export default {
  props: ['title', 'todos', 'id'],
  components: {
    TodoItem,
    CreateNewTodo
  },
  methods: {
    deleteTodo (todo) {
      const itemIndex = this.todos.indexOf(todo)
      this.todos.splice(itemIndex, 1)
    },
    addTodo (newStr) {
      var newID = 0
      if (this.todos.length !== 0) {
        newID = this.todos.reduce((a, b) => (Number(a.id) > Number(b.id) ? a : b)) + 1
      }

      var newTodo = {
        id: newID,
        text: newStr,
        checked: false
      }
      this.todos.push(newTodo)
    },
    deleteList (id) {
      this.$emit('delete-list', id)
    }
  }
}
</script>

<style scoped>
ul {
  list-style-type: none;
  padding: 0;
}
div {
  width: 25em;
}
</style>
