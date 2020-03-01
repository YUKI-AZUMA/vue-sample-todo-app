<template>
  <div class="todo-item">
    <input type="checkbox" v-model="todo.isDone" />
    <span :class="{ done: todo.isDone }">{{ todo.title }}</span>
    <button>編集</button>
    <button @click="deleteItem()">削除</button>
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
  },
  methods: {
    deleteItem() {
      this.$emit('delete')
    }
  }
})
</script>

<style scoped lang="scss">
.todo-item {
  display: flex;
  justify-content: center;
  align-items: center;
}
span.done {
  text-decoration: line-through;
}
</style>
