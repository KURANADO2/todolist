<template>
  <div>
    <label>
      <input v-model="inputValue"/>
    </label>
    <button @click="handleClick">添加</button>
    <ul>
      <todo-item v-for="(item, index) of list" :key="index" :content="item" :index="index" @delete="handleDelete"></todo-item>
    </ul>
  </div>
</template>

<script>
import TodoItem from './components/TodoItem'
export default {
  data: function () {
    return {
      inputValue: '',
      list: []
    }
  },
  components: {
    'todo-item': TodoItem
  },
  methods: {
    handleClick: function () {
      if (this.inputValue === '') {
        return
      }
      this.list.push(this.inputValue)
      this.inputValue = ''
    },
    handleDelete: function (index) {
      this.list.splice(index, 1)
    }
  }
}
</script>

<style>
</style>
