<template>
  <v-card>
    <div v-if="newList">
      <input v-model="newListName" type="text" defaultValue="" style="width: 60%" />
      <v-btn v-on:click="addNewTodoList" color="info" style="width: 40%">
        Add
      </v-btn>
    </div>
    <div v-else>
      <v-btn v-on:click="unfold" color="primary" style="width: 100%">
        New List
      </v-btn>
    </div>
  </v-card>
</template>

<script>
export default {
  data () {
    return {
      newList: false,
      newListName: ''
    }
  },
  methods: {
    addNewTodoList: function () {
      console.log(this.newListName)
      if (this.newListName !== '') {
        this.$emit('new-todo-list', this.newListName)
      }
      this.newListName = ''
      this.newList = false
    },
    unfold: function () {
      this.newList = true
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
