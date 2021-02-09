<template>
  <li>
    <div v-if="newItem">
      <input v-model="newStr" type="text" defaultValue="" />
      <button v-on:click="addItem">Add</button>
    </div>
    <div v-else>
      <button v-on:click="unfold">New Todo</button>
    </div>
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
