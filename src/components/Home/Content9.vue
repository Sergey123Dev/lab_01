<script setup>
import { ref, computed } from 'vue';

// 2. computed() з реальним використанням: Фільтрація списку товарів
// Реактивний список товарів
const products = ref([
  { name: 'Ноутбук', price: 1500 },
  { name: 'Телефон', price: 800 },
  { name: 'Навушники', price: 150 },
]);

// Реактивний пошуковий запит
const searchQuery = ref('');

// Обчислюване значення для фільтрації
const filteredProducts = computed(() => {
  return products.value.filter(product =>
      product.name.toLowerCase().includes(searchQuery.value.toLowerCase())
  );
});
</script>

<template>
  <div>
    <h2>Фільтрація товарів</h2>
    <input v-model="searchQuery" placeholder="Пошук товарів..." />
    <ul>
      <li v-for="product in filteredProducts" :key="product.name">
        {{ product.name }} - ${{ product.price }}
      </li>
    </ul>
  </div>
</template>
