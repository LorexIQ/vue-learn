<template>
  <div>
    <ul>
      <Item
        v-for="(item, i) of list_items"
        v-bind:item="item"
        v-bind:index="i"
        @remove-item="removeItem"
      />
    </ul>
  </div>
</template>

<script>
import Item from '@/components/Item'
export default {
  name: "List",
  props: [
      'list_items',
  ],
  methods: {
    removeItem(id) {
      this.$emit('delete-item', id)
    },
  },
  components: {
    Item,
  },
}
</script>

<style scoped>
ul {
  list-style-type: none;
  padding: 0;
}

li {
  border: 1px solid;
  margin: 5px 0;
  padding: 5px 10px;
  display: flex;
  justify-content: space-between;
}
</style>