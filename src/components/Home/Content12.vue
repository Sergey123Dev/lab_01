<script setup>
import { reactive, watch } from 'vue';

//6. watch() з реальним використанням: Відстеження змін у реактивному об'єкті
// Реактивний об'єкт для форми
const form = reactive({
  name: '',
  email: '',
});

// Відстеження змін у формі
watch(() => form, (newForm, oldForm) => {
  console.log('Зміни в формі:', newForm);
}, { deep: true });
</script>

<template>
  <div>
    <h2>Відстеження змін у формі</h2>
    <form>
      <label>Ім'я</label>
      <input v-model="form.name" />

      <label>Електронна пошта</label>
      <input v-model="form.email" />
    </form>
  </div>
</template>
