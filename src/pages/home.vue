<template>
  <h1>home page</h1>
  <h3>you rate: {{score}}</h3>
  <Rate v-model="score" />
</template>
<script setup>
import { ref } from 'vue';
import Rate from '../components/Rate.vue';
let score = ref(3.5)
</script>