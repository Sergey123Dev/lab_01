<script setup>
import { ref } from 'vue';

//1. ref() з реальним використанням: Реактивний таймер
// Створюємо лічильник для секунд і статус таймера
const seconds = ref(0);
const isRunning = ref(false);
let timer = null;

// Функція для запуску таймера
const startTimer = () => {
  if (!isRunning.value) {
    isRunning.value = true;
    timer = setInterval(() => {
      seconds.value++;
    }, 1000);
  }
};

// Функція для зупинки таймера
const stopTimer = () => {
  isRunning.value = false;
  clearInterval(timer);
};

// Функція для скидання таймера
const resetTimer = () => {
  stopTimer();
  seconds.value = 0;
};
</script>

<template>
  <div>
    <h2>Таймер на Vue 3</h2>
    <p>Пройшло часу: {{ seconds }} секунд</p>
    <button @click="startTimer" :disabled="isRunning">Старт</button>
    <button @click="stopTimer" :disabled="!isRunning">Стоп</button>
    <button @click="resetTimer">Скинути</button>
  </div>
</template>
