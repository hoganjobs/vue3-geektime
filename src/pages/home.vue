<template>
  <h1>home page</h1>
  <TodoList />
  <div>x:{{ x }} | y:{{ y }}</div>
  <StyleBind />
</template>
<script setup>
import TodoList from '../components/TodoList.vue';
import StyleBind from '../components/StyleBind.vue';
import { useMouse } from '../utils/mouse';

let { x, y } = useMouse()
</script>