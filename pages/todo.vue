<script setup>
import { ref, computed } from 'vue'

let id = 0

const newTodo = ref('')
const hideCompleted = ref(false)
const sorted = ref(false)
const todos = ref([
  { id: id++, text: 'Learn HTML', done: true },
  { id: id++, text: 'Learn JavaScript', done: true },
  { id: id++, text: 'Learn Vue', done: false },
  { id: id++, text: 'Learn to learn', done: false },
])

const sortedFilteredTodos = computed(() => {
  if (hideCompleted.value && sorted.value) {
    return todos.value.filter((todo) => !todo.done).sort((a, b) => (a.text > b.text ? 1 : -1))
  } else if (sorted.value) {
    return todos.value.sort((a, b) => (a.text > b.text ? 1 : -1))
  } else {
    return todos.value
  }
})

function addTodo() {
  todos.value.push({ id: id++, text: newTodo.value, done: false })
  newTodo.value = ''
}

function removeTodo(todo) {
  todos.value = todos.value.filter((t) => t !== todo)
}
</script>

<template>
  <nav>
    <a href="/">Back to Nuxt Playground Home</a>
  </nav>
  <h1>The Classic Todo List</h1>
  <p>Based on one of the Vue.js Tutorial examples.</p>
  <form @submit.prevent="addTodo">
    <input v-model="newTodo">
    <button>Add Todo</button>
  </form>
  <ul class="todos">
    <li v-for="todo in sortedFilteredTodos" :key="todo.id">
      <input type="checkbox" v-model="todo.done">
      <span :class="{ done: todo.done }">{{ todo.text }}</span>
      <button @click="removeTodo(todo)">X</button>
    </li>
  </ul>
  <div class="button-group">
    <button @click="hideCompleted = !hideCompleted">
      {{ hideCompleted ? 'Show all' : 'Hide completed' }}
    </button>
    <button @click="sorted = !sorted">
      {{ sorted ? 'Unsort' : 'Sort' }}
    </button>
  </div>
</template>

<style>
ul.todos {
  list-style-type: none;
  padding-left: 0rem;
}

.done {
  text-decoration: line-through;
}

.button-group {
  display: flex;
  gap: 1rem;
}
</style>