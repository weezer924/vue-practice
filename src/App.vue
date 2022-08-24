<template>
  <h1>ToDo App</h1>
  <input type="text" v-model="newTodoText" /><button @click="addTodo">追加</button><button @click="clearDoneTodos">完了済みを削除する</button>
  <ul>
    <p v-if="todos.length === 0">ToDoがありません</p>
    <li v-for="todo in todos" v-bind:key="todo.id">
      <input type="checkbox" v-model="todo.isDone" /><span :class="{ 'todo-done': todo.isDone }">{{ todo.text }}</span>
    </li>
  </ul>
</template>

<script>
export default {
  data() {
    return {
      newTodoText: '',
      todos: []
    }
  },
  methods: {
    addTodo() {
      if(this.newTodoText === '') {
        alert('文字を入力してください')
        return;
      }
      this.todos.push({
        isDone: false,
        text: this.newTodoText
      })
      this.newTodoText = ''
    },
    clearDoneTodos() {
      this.todos = this.todos.filter((todo) => !todo.isDone)
    },
  }
}
</script>

<style>
body {
  background-color: #eee;
}

.todo-done {
  text-decoration: line-through;
}
</style>
