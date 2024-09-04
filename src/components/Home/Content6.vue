<script setup>
import { ref } from 'vue';

const imageUrl = ref('https://via.placeholder.com/150');
const altText = ref('Приклад зображення');
</script>

<template>
  <div>
    <h2>Приклад використання v-bind</h2>
    <img :src="imageUrl" :alt="altText" />
  </div>
</template>
