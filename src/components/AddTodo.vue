<template>
  <div>
    <form v-on:submit.prevent="addTodo">
      <input type="text" name="title" placeholder="Add todo..." v-model="title" />
      <input type="submit" value="Submit" class="btn" />
    </form>
  </div>
</template>

<script>
//import {v4 as uuidv4} from 'uuid';

export default {
  name: "AddTodo",
  data() {
    return {
      title: ''
    }
  },
  methods: {
    addTodo() {
      const newTodo = {
        title: this.title,
        completed: false
      }
      // Send up to parent
      this.$emit('add-todo', newTodo);

      // Clear input todo after successful add
      this.title = '';
    }
  }
}
</script>

<style scoped>
form {
  display: flex;
}

input[type="text"] {
  flex: 11;
  font-size: 16px;
  padding: 10px;
  border: none;
}

input[type="submit"] {
  flex: 1;
  font-size: 16px;
  font-weight: bold;
}
</style>
