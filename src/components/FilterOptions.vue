<template>
  <div>
    <button @click="changeFilter('all')"> All </button>
    <button @click="changeFilter('actives')"> Actives </button>
    <button @click="changeFilter('completed')"> completed </button>
  </div>
</template>
<script>
export default {
  name: 'FilterOptions',
  methods: {
    changeFilter(nameFilter) {
      this.$emit('change-filter', nameFilter)    
    }
  }
}
</script>