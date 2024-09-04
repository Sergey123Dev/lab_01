<script setup>
import {ref} from 'vue'
import Content1 from '../components/Home/Content1.vue'
import Content2 from '../components/Home/Content2.vue'
import Content3 from '../components/Home/Content3.vue'
import Content4 from '../components/Home/Content4.vue'
import Content5 from '../components/Home/Content5.vue'
import Content6 from '../components/Home/Content6.vue'
import Content7 from '../components/Home/Content7.vue'
import Content8 from '../components/Home/Content8.vue'
import Content9 from '../components/Home/Content9.vue'
import Content10 from '../components/Home/Content10.vue'
import Content11 from '../components/Home/Content11.vue'
import Content12 from '../components/Home/Content12.vue'
import Content13 from '../components/Home/Content13.vue'
import Content14 from '../components/Home/Content14.vue'
import Content15 from '../components/Home/Content15.vue'

// Масив компонентів контенту
const contentComponents = [
  Content1, Content2, Content3, Content4, Content5, Content6, Content7,
 Content8 , Content9 , Content10 , Content11 , Content12 , Content13 , Content14 , Content15 ,
];

// Створення реактивного масиву для контролю відкриття/закриття
const isOpenArray = ref(Array(contentComponents.length).fill(false));

// Функція для перемикання стану відкриття/закриття пунктів
const toggleOpen = (index) => {
  isOpenArray.value[index] = !isOpenArray.value[index];
}
</script>

<template>
  <div>
    <!-- Генерація пунктів за допомогою v-for -->
    <div v-for="(ContentComponent, index) in contentComponents" :key="index">
      <h1 @click="toggleOpen(index)" style="cursor: pointer;">Пункт {{ index + 1 }} (натисни для відкриття)</h1>
      <div v-if="isOpenArray[index]">
        <component :is="ContentComponent"/>
      </div>
    </div>
  </div>
</template>

<style scoped>
h1 {
  margin: 1rem 0;
  cursor: pointer;
}
</style>
