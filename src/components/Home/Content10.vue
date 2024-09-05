<script setup>
import { reactive } from 'vue';

// reactive() з реальним використанням: Управління формою
// Реактивний об'єкт для форми
const form = reactive({
  name: '',
  email: '',
  message: '',
});

// Функція для обробки надсилання форми
const submitForm = () => {
  alert(`Форма надіслана! Ім'я: ${form.name}, Електронна пошта: ${form.email}, Повідомлення: ${form.message}`);
};
</script>

<template>
  <div>
    <h2>Форма з використанням reactive</h2>
    <form @submit.prevent="submitForm">
      <label>Ім'я</label>
      <input v-model="form.name" />

      <label>Електронна пошта</label>
      <input v-model="form.email" />

      <label>Повідомлення</label>
      <textarea v-model="form.message"></textarea>

      <button type="submit">Надіслати</button>
    </form>
  </div>
</template>
