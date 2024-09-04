<script setup>
import {ref, onBeforeMount, onMounted, onBeforeUpdate, onUpdated, onBeforeUnmount, onUnmounted} from 'vue';

const counter = ref(0);

// Виведення життєвих циклів в консоль
onBeforeMount(() => {
  console.log('onBeforeMount: Компонент ще не змонтований.');
});

onMounted(() => {
  console.log('onMounted: Компонент змонтований.');
});

onBeforeUpdate(() => {
  console.log('onBeforeUpdate: Компонент збирається оновитися.');
});

onUpdated(() => {
  console.log('onUpdated: Компонент оновлений.');
});

onBeforeUnmount(() => {
  console.log('onBeforeUnmount: Компонент збирається бути знищеним.');
});

onUnmounted(() => {
  console.log('onUnmounted: Компонент знищений.');
});

// Логіка збільшення лічильника
const incrementCounter = () => {
  counter.value++;
};
</script>

<template>
  <div>
    <h2>Демонстрація життєвого циклу Vue з Composition API</h2>
    <p>Лічильник: {{ counter }}</p>
    <button @click="incrementCounter">Збільшити лічильник</button>
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

button:hover {
  background-color: #0056b3;
}
</style>
