<template>
  <div>
    <h1>Todoリスト</h1>
    <input v-model="newTodo" />
    <button @click="addItem">追加！</button>
    <TodoItemList
      class="todo-item-list"
      :todoList="todoList"
      @delete="deleteItem($event)"
    />
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
      newTodo: '',
      todoList: []
    }
  },
  methods: {
    addItem() {
      this.todoList.push({
        uid: Math.random()
          .toString(32)
          .substring(2),
        title: this.newTodo,
        isDone: false,
        createdAt: new Date()
      })
      this.newTodo = ''
    },
    deleteItem(index) {
      this.todoList.splice(index, 1)
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
