<script setup>
let id = 0
const todos = ref([
  { id: id++, text: 'Learn HTML', done: true },
  { id: id++, text: 'Learn JavaScript', done: true },
  { id: id++, text: 'Learn Vue', done: false },
  { id: id++, text: 'Rest', done: false },
  { id: id++, text: 'Hello World!', done: true },
])

const newTodoText = ref('')
const hideCompleted = ref(false)
const sorted = ref(false)

const filteredSortedTodos = computed(() => todos.value.filter((todo) => !todo.done).sort((a, b) => (a.text > b.text ? 1 : -1)))
const filteredTodos = computed(() => todos.value.filter((todo) => !todo.done))
const sortedTodos = computed(() => [...todos.value].sort((a, b) => (a.text > b.text ? 1 : -1)))

const anyTodoDone = computed(() => todos.value.filter((todo) => todo.done).length > 0)
const anyTodoToSort = computed(() => hideCompleted.value ? filteredTodos.value.length > 1 : todos.value.length > 1)

function addTodo() {
  todos.value.push({ id: id++, text: newTodoText.value, done: false })
  newTodoText.value = ''
}

const renderedTodos = computed(() => {
  if (hideCompleted.value) {
    return sorted.value ? filteredSortedTodos.value : filteredTodos.value
  } else {
    return sorted.value ? sortedTodos.value : todos.value
  }
})
</script>

<template>
  <nav>
    <a href="/">Back to Nuxt Playground Home</a>
  </nav>
  <h1>The Classic Todo List</h1>
  <p>Based on one of the Vue.js Tutorial examples.</p>
  <form @submit.prevent="addTodo">
    <input v-model="newTodoText">
    <button>Add Todo</button>
  </form>
  <div class="button-group">
    <button @click="hideCompleted = !hideCompleted" :disabled="!anyTodoDone">
      {{ hideCompleted ? 'Show all' : 'Hide completed' }}
    </button>
    <button @click="sorted = !sorted" :disabled="!anyTodoToSort">
      {{ sorted ? 'Unsort' : 'Sort' }}
    </button>
  </div>
  <ul class="todos">
    <TodoItem v-for="todo in renderedTodos" :key="todo.id" :text="todo.text" :done="todo.done"
      @remove="todos = todos.filter((t) => t !== todo)" @done="todo.done = !todo.done" />
  </ul>
</template>

<style>
form {
  padding-block: .5rem;
}

ul.todos {
  list-style-type: none;
  padding-left: 0rem;
}

li {
  padding-block: .25rem;
}

.done {
  text-decoration: line-through;
}

.removebutton {
  margin-left: .25rem;
}

.button-group {
  display: flex;
  gap: 1rem;
  padding-block: .5rem;
}
</style>