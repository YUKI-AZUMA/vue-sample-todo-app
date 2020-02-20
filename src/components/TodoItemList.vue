<template>
  <div>
    <TodoItem v-for="(todo, index) in todoList" :key="index" :todo="todo" />
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
  }
})
</script>
