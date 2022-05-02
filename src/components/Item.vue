<template>
  <li>
    <span v-bind:class="{completed: item.completed}">
      <input type="checkbox" :checked="item.completed" v-on:change="item.completed = !item.completed">
      <strong class="id">{{index + 1}}</strong>
      {{item.title}}
    </span>
    <button v-on:click="$emit('remove-item', item.id)">&times;</button>
  </li>
</template>

<script>
export default {
  name: "Item",
  props: {
    item: {
      type: Object,
      required: true,
    },
    index: Number,
  },
}
</script>

<style scoped>
.id {
  padding: 0 0.2rem 0 1rem;
}

button {
  border-radius: 100%;
  padding-top: 2px;
  color: #fff;
  background-color: #cf4832;
  border: 1px solid #000;
}

.completed {
  text-decoration: line-through;
}
</style>