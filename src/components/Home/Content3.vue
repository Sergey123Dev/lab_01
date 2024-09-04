<script setup>
import { ref } from 'vue';

const items = ref(['Пункт 1', 'Пункт 2', 'Пункт 3']);
</script>

<template>
  <div>
    <h2>Приклад використання v-for</h2>
    <ul>
      <li v-for="(item, index) in items" :key="index">{{ index + 1 }}. {{ item }}</li>
    </ul>
  </div>
</template>
