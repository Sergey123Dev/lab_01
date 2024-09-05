<script setup>
import { ref, watchEffect } from 'vue';

//5. watchEffect() з реальним використанням: Відстеження розмірів вікна
// Створюємо реактивні змінні для висоти та ширини
const windowWidth = ref(window.innerWidth);
const windowHeight = ref(window.innerHeight);

// Використовуємо watchEffect для відстеження зміни розміру вікна
watchEffect(() => {
  const updateWindowSize = () => {
    windowWidth.value = window.innerWidth;
    windowHeight.value = window.innerHeight;
  };
  window.addEventListener('resize', updateWindowSize);

  // Очищення, коли компонент демонтується
  return () => {
    window.removeEventListener('resize', updateWindowSize);
  };
});
</script>

<template>
  <div>
    <h2>Розмір вікна</h2>
    <p>Ширина: {{ windowWidth }} px</p>
    <p>Висота: {{ windowHeight }} px</p>
  </div>
</template>
