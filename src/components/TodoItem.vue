<template>
  <li>
    <input type="checkbox" id="checkbox" v-model="todo.checked" />
    <div v-if="todo.checked">
      <s>{{ todo.text }}</s>
    </div>
    <div v-else>{{ todo.text }}</div>
    <button v-on:click="todoDelete(todo)">Delete</button>
  </li>
</template>

<script>
export default {
  props: ['todo'],
  methods: {
    todoDelete: function (todo) {
      this.$emit('delete-todo', todo)
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
li {
  display: block;
  margin: 0 10px;
  text-align: center;
}
div {
  display: inline;
}
a {
  color: #42b983;
}
</style>
