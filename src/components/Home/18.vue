<script setup>
// Функція для генерації випадкового кольору
const getRandomColor = () => {
  const letters = '0123456789ABCDEF';
  let color = '#';
  for (let i = 0; i < 6; i++) {
    color += letters[Math.floor(Math.random() * 16)];
  }
  return color;
};

// Директива для зміни кольору фону при наведенні
const vHover = {
  mounted(el) {
    el.addEventListener('mouseenter', () => {
      el.style.backgroundColor = getRandomColor();
    });
    el.addEventListener('mouseleave', () => {
      el.style.backgroundColor = ''; // Повертаємо до початкового стану
    });
  },
};

</script>

<template>
  <div>
    <p v-hover>
      Наведіть на цей текст після його затриманого відображення, щоб змінити фон на випадковий колір.
    </p>
  </div>
</template>

<style scoped>
p {
  padding: 1rem;
  background-color: lightgray;
  border: 1px solid #ccc;
  cursor: pointer;
  transition: background-color 0.3s ease; /* Плавний перехід кольору */
}
</style>
