<template>
  <h1>home page</h1>
  <h3>you rate: {{score}}</h3>
  <Rate :value="score" @updateRate="update" />
</template>
<script setup>
import { ref } from 'vue';
import Rate from '../components/Rate.vue';
let score = ref(3.5)
function update(num) {
  score.value = num
}
</script>