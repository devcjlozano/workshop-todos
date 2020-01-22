<template>
  <div>
    <ul>
      <li
        v-for="todo in listTodos"
        :key="todo.id"> 
      <span :class="{'completed': todo.completed}"> {{ todo.name }} </span>
      <button @click="completeTodo(todo.id)"> X </button>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'ListTodos',
  props: {
    listTodos: {
       type: Array,
       default: () => []
    }
  },
  methods: {
      completeTodo(idTodo) {
       this.$emit('complete-todo', idTodo)
      }
  }
}
</script>
<style scoped>
  .completed {
     text-decoration: line-through;
  }
</style>