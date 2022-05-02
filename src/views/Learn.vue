<template>
  <div>
    <h2>List</h2>
    <router-link to="/">Home</router-link>
    <hr>
    <Add
        @new-item="addItem"
    />
    <hr>
    <select v-model="filter">
      <option value="all">Всё</option>
      <option value="done">Выполнено</option>
      <option value="not-done">Не выполнено</option>
    </select>
    <List
        v-if="filteredItems.length"
        v-bind:list_items="filteredItems"
        @delete-item="deleteItem"
        @new-item="addItem"
    />
    <p v-else>Список пуст</p>
  </div>
</template>

<script>
import List from '@/components/List'
import Add from '@/components/Add'
export default {
  name: 'Learn',
  data() {
    return {
      list_items: [],
      filter: 'all',
    }
  },
  mounted() {
    fetch('https://jsonplaceholder.typicode.com/todos?_limit=10')
        .then(response => response.json())
        .then(json => {
          this.list_items = json
        })
  },
  methods: {
    deleteItem(id) {
      this.list_items = this.list_items.filter(i => i.id !== id)
    },
    addItem(new_item) {
      this.list_items.push(new_item)
    }
  },
  computed: {
    filteredItems() {
      if (this.filter === 'all') {
        return this.list_items
      }
      if (this.filter === 'done') {
        return this.list_items.filter(i => i.completed)
      }
      return this.list_items.filter(i => !i.completed)
    }
  },
  components: {
    List, Add,
  },
}
</script>

<style scoped>

</style>