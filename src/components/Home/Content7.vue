<script setup>
const handleClick = () => {
  alert('Кнопку натиснуто!');
};
</script>

<template>
  <div>
    <h2>Приклад використання v-on</h2>
    <button @click="handleClick">Натисни мене</button>
  </div>
</template>

<style scoped>
button {
  padding: 0.5rem 1rem;
  background-color: #007bff;
  color: white;
  border: none;
  cursor: pointer;
}

button:hover {
  background-color: #0056b3;
}
</style>
