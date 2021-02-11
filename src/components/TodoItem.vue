<template>
    <li>
      <v-card>
        <v-row align="center">
          <v-col align="center">
              <v-checkbox
                v-model="todo.checked"
                color="primary"
                value="primary"
                hide-details
              ></v-checkbox>
          </v-col>
          <v-col>
            <div v-if="todo.checked">
              <s>{{ todo.text }}</s>
            </div>
            <div v-else>{{ todo.text }}</div>
          </v-col>
          <v-col>
            <v-btn
                icon
                color="red"
                v-on:click="todoDelete(todo)"
              >
                <v-icon>mdi-delete</v-icon>
              </v-btn>
          </v-col>
        </v-row>
      </v-card>
    </li>
</template>

<script>
export default {
  props: ['todo'],
  methods: {
    todoDelete (todo) {
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

a {
  color: #42b983;
}
</style>
