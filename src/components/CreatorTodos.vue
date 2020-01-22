<template>
   <div>
      <input
        v-model="nameTodo" 
        type="text"/>
      <button @click="createTodo"> add todo </button>
   </div> 
</template>
<script>
export default {
  name: 'CreatorTodos',
  data() {
    return {
        nameTodo: ''
    }
  },
  methods: {
     createTodo() {
        this.$emit('create-todo', this.nameTodo) 
     }
  }
}
</script>