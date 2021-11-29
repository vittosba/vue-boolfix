<template>
  <header>
      <input type="text" v-model.trim="searchText" @keyup.enter="$emit('performSearch', searchText)">
      <button @click.prevent="$emit('performSearch', searchText)">Search</button>
  </header>
</template>

<script>
export default {
    name: 'Header',
    data() {
        return {
            searchText: '',
        }
    }
}
</script>

<style>

</style>