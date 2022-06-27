<template>
  <div>
    <input type="text" v-model="title" @keydown.enter="addTodo" />
    <button v-if="active < all" @click="clear">clear</button>
    <ul v-if="todos.length">
      <li v-for="todo in todos">
        <input type="checkbox" v-model="todo.done" />
        <span :class="{ done: todo.done }">{{ todo.title }}</span>
      </li>
    </ul>
    <div v-else>no data</div>
    <div>
      select all
      <input type="checkbox" v-model="allDone">
      <span>{{ active }}/{{ all }}</span>
    </div>
  </div>
</template>
<script setup>
import { ref, computed, watchEffect } from 'vue';

let { title, todos, addTodo, clear, active, all, allDone } = useTodos();

function useTodos() {
  let title = ref("")
  let todos = useStorage('todos', [])

  function useStorage(name, value = []) {
    let data = ref(JSON.parse(localStorage.getItem(name) || value))
    watchEffect(() => {
      localStorage.setItem(name, JSON.stringify(data.value))
    })
    return data
  }
  function addTodo() {
    todos.value.push({
      title: title.value,
      done: false
    })
    title.value = ""
  }
  function clear() {
    todos.value = todos.value.filter((v) => !v.done)
  }
  let active = computed(() => {
    return todos.value.filter((v) => !v.done).length
  })
  let all = computed(() => {
    return todos.value.length
  })
  let allDone = computed({
    get: function () {
      return active.value === 0
    },
    set: function (value) {
      todos.value.forEach(todo => {
        todo.done = value
      });
    }
  })
  return { title, todos, addTodo, clear, active, all, allDone }
}
</script>
