<template>
  <div class="todo-item">
    <input type="checkbox" />
    <p>{{ todo.title }}</p>
    <p>{{ todo.isDone }}</p>
    <button>編集</button>
    <button>削除</button>
  </div>
</template>

<script lang="ts">
import Vue, { PropType } from 'vue'
import { Todo } from '../../types'

export default Vue.extend({
  props: {
    todo: {
      type: Object as PropType<Todo>,
      required: true
    }
  }
})
</script>

<style scoped lang="scss">
.todo-item {
  display: flex;
}
</style>
