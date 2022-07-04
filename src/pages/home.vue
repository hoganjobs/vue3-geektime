<template>
  <h1>home page</h1>
  <Rate :value="score" />
</template>
<script setup>
import { ref } from 'vue'
import Rate from '../components/Rate.vue';
let score = ref(3)
</script>