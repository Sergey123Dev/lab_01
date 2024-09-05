<script setup>
import { ref, onMounted, onUnmounted } from 'vue';

const gridSize = 20;
const initialSnake = [42, 41, 40]; // Початкові позиції змійки
const grid = new Array(gridSize * gridSize).fill(null); // Створення сітки

const snake = ref([...initialSnake]);
const foodPosition = ref(Math.floor(Math.random() * grid.length)); // Випадкове розташування їжі
const direction = ref('right');
const gameOver = ref(false);

// Функція для руху змійки
const moveSnake = () => {
  const head = snake.value[0];
  let newHead;

  switch (direction.value) {
    case 'up':
      newHead = head - gridSize;
      break;
    case 'down':
      newHead = head + gridSize;
      break;
    case 'left':
      newHead = head - 1;
      break;
    case 'right':
      newHead = head + 1;
      break;
  }

  // Перевірка на стіну або на саму себе
  if (
      newHead < 0 || newHead >= gridSize * gridSize || // Вихід за межі сітки
      (direction.value === 'left' && head % gridSize === 0) || // Ліва стіна
      (direction.value === 'right' && head % gridSize === gridSize - 1) || // Права стіна
      snake.value.includes(newHead) // Вдарила сама себе
  ) {
    gameOver.value = true;
    return;
  }

  snake.value.unshift(newHead); // Додаємо нову голову змійки

  // Якщо змійка з'їла їжу
  if (newHead === foodPosition.value) {
    placeFood();
  } else {
    snake.value.pop(); // Змійка рухається, видаляємо останній елемент
  }
};

// Розміщення їжі в новій випадковій позиції
const placeFood = () => {
  let newPosition;
  do {
    newPosition = Math.floor(Math.random() * grid.length);
  } while (snake.value.includes(newPosition));
  foodPosition.value = newPosition;
};

// Зміна напрямку руху
const handleKeyDown = (event) => {
  switch (event.key) {
    case 'ArrowUp':
      if (direction.value !== 'down') direction.value = 'up';
      break;
    case 'ArrowDown':
      if (direction.value !== 'up') direction.value = 'down';
      break;
    case 'ArrowLeft':
      if (direction.value !== 'right') direction.value = 'left';
      break;
    case 'ArrowRight':
      if (direction.value !== 'left') direction.value = 'right';
      break;
    case 'r':
    case 'R':
      resetGame();
      break;
  }
};

// Перезапуск гри
const resetGame = () => {
  snake.value = [...initialSnake];
  foodPosition.value = Math.floor(Math.random() * grid.length);
  direction.value = 'right';
  gameOver.value = false;
};

// Гра починається, змійка рухається кожні 200 мс
let gameInterval;
onMounted(() => {
  gameInterval = setInterval(() => {
    if (!gameOver.value) {
      moveSnake();
    }
  }, 200);
  window.addEventListener('keydown', handleKeyDown);
});

// Зупинка гри при демонтажі компонента
onUnmounted(() => {
  clearInterval(gameInterval);
  window.removeEventListener('keydown', handleKeyDown);
});
</script>

<template>
  <div class="game">
    <h1>Гра: Змійка</h1>
    <div class="grid">
      <div
          v-for="index in gridSize * gridSize"
          :key="index"
          class="cell"
          :class="{ snake: snake.includes(index - 1), food: foodPosition === index - 1 }"
      ></div>
    </div>
    <p v-if="gameOver">Гра завершена! Натисніть R для рестарту.</p>
  </div>
</template>

<style scoped>
.game {
  display: flex;
  flex-direction: column;
  align-items: center;
  margin-top: 50px;
}

.grid {
  display: grid;
  grid-template-columns: repeat(20, 20px);
  grid-template-rows: repeat(20, 20px);
  gap: 2px;
}

.cell {
  width: 20px;
  height: 20px;
  background-color: #f0f0f0;
  border: 1px solid #ccc;
}

.snake {
  background-color: green;
}

.food {
  background-color: red;
}

p {
  margin-top: 20px;
  font-size: 18px;
  font-weight: bold;
}
</style>
