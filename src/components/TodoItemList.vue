<template>
  <div lass="todo-item-list">
    <TodoItem
      v-for="(todo, index) in todoList"
      :key="index"
      :todo="todo"
      @delete="deleteItem(index)"
      @update="updateItem($event, index)"
    />
  </div>
</template>

<script lang="ts">
import Vue, { PropType } from 'vue'
import TodoItem from '../components/TodoItem.vue'
import { Todo } from '../../types'

export default Vue.extend({
  components: {
    TodoItem
  },
  props: {
    todoList: {
      type: Array as PropType<Todo[]>,
      required: true
    }
  },
  methods: {
    deleteItem(index: BigInteger) {
      this.$emit('delete', index)
    },
    updateItem(updateTodo: String, index: BigInteger) {
      this.$emit('update', { index, updateTodo })
    }
  }
})
</script>

<style scoped lang="scss">
.todo-item-list {
  display: flex;
  flex-direction: column;
  flex-wrap: wrap;
}
</style>
