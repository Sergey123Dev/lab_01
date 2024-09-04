<script setup>
import { ref } from 'vue';

const isVisible = ref(true);

const toggleVisibility = () => {
  isVisible.value = !isVisible.value;
};
</script>

<template>
  <div>
    <h2>Приклад використання v-show</h2>
    <button @click="toggleVisibility">
      {{ isVisible ? 'Сховати' : 'Показати' }} повідомлення
    </button>
    <p v-show="isVisible">Це повідомлення видно завжди в DOM, але його можна приховати.</p>
  </div>
</template>

<style scoped>
button {
  margin-bottom: 1rem;
}
</style>
