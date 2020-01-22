<template>
  <div class="home">
    <CreatorTodos
      @create-todo="createTodo"/>
    <FilterOptions
    @change-filter="changeFilter"/>
    <span> Filtro seleccionado: {{nameFilter}} </span>
    <ListTodos
     :list-todos="filterListTodos"
     @complete-todo="completeTodo"/>
  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from '@/components/HelloWorld.vue'
import CreatorTodos from '@/components/CreatorTodos.vue'
import FilterOptions from '@/components/FilterOptions.vue'
import ListTodos from '@/components/ListTodos.vue'

export default {
  name: 'home',
  components: {
    CreatorTodos,
    FilterOptions,
    ListTodos
  },
  data() {
    return {
      listTodos: [
        {
          name: 'Aprender Vue',
          completed: false,
          id: 1
        },
        {
          name: 'Comprar',
          completed: false,
          id: 2
        }
      ],
      nameFilter: 'all'
    }
  },
  computed: {
    filterListTodos() {
      if (this.nameFilter === 'actives') {
        return this.listTodos.filter(todo => !todo.completed)
      }
      if (this.nameFilter === 'completed') {
        return this.listTodos.filter(todo => todo.completed)
      }
      return this.listTodos
    }
  },
  methods: {
    createTodo(nameTodo) {
      const newTodo = {
        name: nameTodo,
        completed: false,
        id: Date.now()
      }
      this.listTodos.push(newTodo)
    },
    completeTodo(idTodo) {
      const indexTodo = this.listTodos.findIndex(todo => todo.id === idTodo)
      this.listTodos[indexTodo].completed = !this.listTodos[indexTodo].completed
    },
    changeFilter(nameFilter) {
      this.nameFilter = nameFilter;
    }
  }
}
</script>