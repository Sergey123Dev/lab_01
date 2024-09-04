<script setup>
import { ref } from 'vue';

const isVisible = ref(true);

const toggleVisibility = () => {
  isVisible.value = !isVisible.value;
};
</script>

<template>
  <div>
    <h2>Приклад використання v-if / v-else</h2>
    <button @click="toggleVisibility">
      {{ isVisible ? 'Сховати' : 'Показати' }} повідомлення
    </button>
    <p v-if="isVisible">Це повідомлення відображається!</p>
    <p v-else>Повідомлення сховане.</p>
  </div>
</template>

<style scoped>
button {
  padding: 0.5rem 1rem;
  margin-top: 1rem;
  background-color: #007bff;
  color: white;
  border: none;
  cursor: pointer;
}
</style>
