<template>
  <form @submit.prevent="onSubmit">
    <input type="text" v-model="title">
    <button type="submit">Добавить</button>
  </form>
</template>

<script>
export default {
  name: "Add",
  data() {
    return {
      title: '',
    }
  },
  methods: {
    onSubmit() {
      if (this.title.trim()) {
        const newItem = {
          id: Date.now(),
          title: this.title,
          completed: false,
        }
        this.$emit('new-item', newItem)
        this.title = ''
      }
    },
  },
}
</script>

<style scoped>
form {
  display: flex;
}

input {
  width: 100%;
}

button {
  margin-left: 10px;
  background-color: #5091e0;
  border: 1px solid #000;
  color: #fff;
}
</style>