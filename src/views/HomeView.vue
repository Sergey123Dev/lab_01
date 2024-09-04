<script setup>
import { ref } from 'vue'

// Створюємо реактивну змінну, яка зберігає стан відкриття/закриття пунктів
const isOpen1 = ref(false)
const isOpen2 = ref(false)

// Функції для перемикання стану відкриття/закриття
const toggleOpen1 = () => {
  isOpen1.value = !isOpen1.value
}

const toggleOpen2 = () => {
  isOpen2.value = !isOpen2.value
}
</script>

<template>
  <div>
    <!-- Пункт 1 -->
    <div>
      <h1 @click="toggleOpen1" style="cursor: pointer;">Пункт 1 (натисни для відкриття)</h1>
      <div v-if="isOpen1">
        <p>Це вміст першого пункту. Він відкривається при натисканні.</p>
      </div>
    </div>

    <!-- Пункт 2 -->
    <div>
      <h1 @click="toggleOpen2" style="cursor: pointer;">Пункт 2 (натисни для відкриття)</h1>
      <div v-if="isOpen2">
        <p>Це вміст другого пункту. Він також відкривається при натисканні.</p>
      </div>
    </div>
  </div>
</template>
