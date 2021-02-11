<template>
  <v-app>
    <v-main>
      <v-row align="start">
        <todo-list
          v-for="todolist in lists"
          v-bind:id="todolist.id"
          v-bind:todos="todolist.todos"
          v-bind:title="todolist.title"
          v-bind:key="todolist.id"
          v-on:delete-list="deleteList"
        ></todo-list>
        <v-col>
          <create-new-todo-list v-on:new-todo-list="addNewTodoList"></create-new-todo-list>
        </v-col>
      </v-row>
    </v-main>
  </v-app>
</template>

<script>
import TodoList from './components/TodoList'
import CreateNewTodoList from './components/CreateNewTodoList'

export default {
  name: 'App',

  components: {
    TodoList,
    CreateNewTodoList
  },

  data () {
    return {
      lists: []
    }
  },
  methods: {
    addNewTodoList (newListName) {
      var newListID = 0
      if (this.lists.length !== 0) {
        newListID = this.lists.reduce((a, b) => (Number(a.id) > Number(b.id) ? a : b)) + 1
      }

      var newList = {
        id: newListID,
        title: newListName,
        todos: []
      }
      this.lists.push(newList)
    },
    deleteList (id) {
      var listIndex
      for (var i = 0; i < this.lists.length; i++) {
        if (this.lists[i].id === id) {
          listIndex = i
          break
        }
      }
      this.lists.splice(listIndex, 1)
    }
  }
}
</script>
