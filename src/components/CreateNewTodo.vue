<template>
  <li>
    <v-card>
      <div v-if="newItem">
        <input v-model="newStr" type="text" defaultValue="" style="width: 60%" />
        <v-btn v-on:click="addItem" color="info" style="width: 40%">
          Add
        </v-btn>
      </div>
      <div v-else>
        <v-btn v-on:click="unfold" color="primary" style="width: 100%">
          New Todo
        </v-btn>
      </div>
    </v-card>
  </li>
</template>

<script>
export default {
  data () {
    return {
      newItem: false,
      newStr: ''
    }
  },
  methods: {
    addItem: function () {
      console.log(this.newStr)
      if (this.newStr !== '') {
        this.$emit('new-todo', this.newStr)
      }
      this.newStr = ''
      this.newItem = false
    },
    unfold: function () {
      this.newItem = true
    }
  }
}
</script>

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
