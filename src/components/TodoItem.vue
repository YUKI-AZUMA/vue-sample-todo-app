<template>
  <div class="todo-item">
    <div v-if="show">
      <input type="checkbox" v-model="todo.isDone" />
      <span :class="{ done: todo.isDone }">{{ todo.title }}</span>
      <button @click="showEditArea()">編集</button>
      <button @click="deleteItem()">削除</button>
    </div>
    <div v-else>
      <input v-model="updateTodo" />
      <button @click="updateItem()">更新</button>
      <button @click="canvelEditArea()">キャンセル</button>
    </div>
  </div>
</template>

<script lang="ts">
import Vue, { PropType } from 'vue'
import { Todo } from '../../types'

export default Vue.extend({
  data() {
    return {
      updateTodo: '',
      show: true
    }
  },
  props: {
    todo: {
      type: Object as PropType<Todo>,
      required: true
    }
  },
  methods: {
    showEditArea() {
      this.show = false
    },
    canvelEditArea() {
      this.show = true
    },
    deleteItem() {
      this.$emit('delete')
    },
    updateItem() {
      this.todo.title = this.updateTodo
      this.$emit('update', this.todo)
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
