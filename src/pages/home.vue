<template>
  <h1>home page</h1>
  <Rate :value="3" />
  <Rate :value="4" theme="red" />
  <Rate :value="1" theme="green" />
</template>
<script setup>
import Rate from '../components/Rate.vue';
</script>