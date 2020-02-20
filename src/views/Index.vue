<template>
  <div>
    <h1>Todoリスト</h1>
    <input v-model="newItem" />
    <button @click="addItem">追加！</button>
    <TodoItemList class="todo-item-list" :todoList="todoList" />
  </div>
</template>

<script>
import TodoItemList from '@/components/TodoItemList.vue'

export default {
  components: {
    TodoItemList
  },

  data() {
    return {
      newItem: '',
      todoList: [],
      todo: {
        uid: 'hoge',
        title: '',
        isDone: false,
        createdAt: new Date()
      }
    }
  },
  methods: {
    addItem: function() {
      this.todo.title = this.newItem
      this.todoList.push(this.todo)
      this.newItem = ''
    }
  }
}
</script>

<style scoped lang="scss">
.todo-item-list {
  display: -webkit-flex;
  -webkit-justify-content: center;
  justify-content: center;
  -webkit-align-items: stretch;
  align-items: stretch;
  text-align: center;
}
</style>
