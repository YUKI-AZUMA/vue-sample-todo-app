<template>
  <div>
    <h1>Todoリスト</h1>
    <form>
      <input v-model="newItem" />
      <button v-on:click="addItem">追加！</button>
    </form>
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
      todoList: [],
      newItem: ''
    }
  },
  methods: {
    addItem: function() {
      var todo = {
        uid: 'hoge',
        title: this.newItem,
        isDone: false,
        createdAt: new Date()
      }
      this.todoList.push(todo)
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
