<script setup>
import { ref } from 'vue';

// Оголошення реактивних змінних
const number1 = ref(10);
const number2 = ref(20);
const text = ref("Привіт, Vue!");
const isVisible = ref(true);
</script>

<template>
  <div>
    <h2>Використання виразів JavaScript у Vue</h2>

    <!-- Простий вираз -->
    <p>Сума чисел: {{ number1 + number2 }}</p>

    <!-- Використання методів -->
    <p>Текст у верхньому регістрі: {{ text.toUpperCase() }}</p>

    <!-- Тернарний оператор -->
    <p>{{ isVisible ? 'Елемент видимий' : 'Елемент прихований' }}</p>

    <!-- Виклик функції в шаблоні -->
    <p>Модуль від'ємного числа: {{ Math.abs(-42) }}</p>

    <!-- Конкатенація рядків -->
    <p>{{ 'Рік: ' + new Date().getFullYear() }}</p>
  </div>
</template>
