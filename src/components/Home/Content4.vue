<script setup>
import { ref } from 'vue';

const text = ref('');
</script>

<template>
  <div>
    <h2>Приклад використання v-model</h2>
    <input v-model="text" placeholder="Введіть щось" />
    <p>Введене значення: {{ text }}</p>
  </div>
</template>

<style scoped>
input {
  padding: 0.5rem;
  margin-top: 1rem;
  display: block;
}
</style>
