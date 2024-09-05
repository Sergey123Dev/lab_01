<script setup>
import { ref } from 'vue'
import Content1 from '../components/Home/1.vue'
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
import Content16 from '../components/Home/Props/ParentComponent.vue'
import Content17 from '../components/Home/17.vue';
import Content18 from '../components/Home/18.vue';
import Content19 from '../components/Home/19.vue';
import Content20 from '../components/Home/20.vue';
import Content21 from '../components/Home/21.vue';
import Content22 from '../components/Home/22.vue';
import Content23 from '../components/Home/23.vue';
import Content24 from '../components/Home/24.vue';
import Content25 from '../components/Home/25.vue';
import Content26 from '../components/Home/26.vue';
import Content27 from '../components/Home/27.vue';
import Content28 from '../components/Home/28.vue';
import Content29 from '../components/Home/29.vue';
import Content30 from '../components/Home/30.vue';
import Content31 from '../components/Home/31.vue';
import Content32 from '../components/Home/32.vue';
import Content33 from '../components/Home/33.vue';
import Content34 from '../components/Home/34.vue';
import Content35 from '../components/Home/35.vue';
import Content36 from '../components/Home/36.vue';
import Content37 from '../components/Home/37.vue';
import Content38 from '../components/Home/38.vue';
import Content39 from '../components/Home/39.vue';
import Content40 from '../components/Home/40.vue';

// Асоціативний масив з компонентами та заголовками
const contentMap = {
  content1: { component: Content1, title: '1. Демонстрація життєвого циклу Vue з Composition API' },
  content16: { component: Content16, title: 'Робота з Props та подіями' },
  content2: { component: Content2, title: '1.1. Директиви: Приклад використання v-if / v-else' },
  content3: { component: Content3, title: '1.2. Директиви: Приклад використання v-for' },
  content4: { component: Content4, title: '1.3. Директиви: Приклад використання v-model' },
  content5: { component: Content5, title: '1.4. Директиви: Приклад використання v-show' },
  content6: { component: Content6, title: '1.5. Директиви: Приклад використання v-bind' },
  content7: { component: Content7, title: '1.6. Директиви: Приклад використання v-on' },
  content8: { component: Content8, title: '2.1 ref()' },
  content9: { component: Content9, title: '2.2 computed()' },
  content10: { component: Content10, title: '2.3 reactive()' },
  content11: { component: Content11, title: '2.4 watchEffect()' },
  content12: { component: Content12, title: '2.5 watch()' },
  content13: { component: Content13, title: '2.4 watchEffect(' },
  content14: { component: Content14, title: 'Example Simple Game' },
  content15: { component: Content15, title: 'Кастомні директиви' },
  content17: { component: Content17, title: 'Використання виразів JavaScript у Vue' },
  content18: { component: Content18, title: '3.2. Валідація форм' },
  content19: { component: Content19, title: '3.3. Обробка подій форм' },
  content20: { component: Content20, title: '3.4. Динамічні форми' },
  content21: { component: Content21, title: '4.1. Динамічний рендеринг' },
  content22: { component: Content22, title: '4.2. Динамічні компоненти' },
  content23: { component: Content23, title: '4.3. Лінива завантаження компонентів' },
  content24: { component: Content24, title: '4.4. Слотинг у Vue' },
  content25: { component: Content25, title: '5.1. Vue Router: Основи' },
  content26: { component: Content26, title: '5.2. Vue Router: Навігація між сторінками' },
  content27: { component: Content27, title: '5.3. Вкладені маршрути' },
  content28: { component: Content28, title: '5.4. Динамічні маршрути' },
  content29: { component: Content29, title: '5.5. Переадресація та затримка' },
  content30: { component: Content30, title: '5.6. Захист маршрутів' },
  content31: { component: Content31, title: '6.1. Vuex: Створення сховища' },
  content32: { component: Content32, title: '6.2. Vuex: Робота з даними в стані' },
  content33: { component: Content33, title: '6.3. Vuex: Мутації та дії' },
  content34: { component: Content34, title: '6.4. Vuex: Геттерси та маппінг стану' },
  content35: { component: Content35, title: '7.1. Фільтри у Vue' },
  content36: { component: Content36, title: '7.2. Міксини' },
  content37: { component: Content37, title: '7.3. Плагіни у Vue' },
  content38: { component: Content38, title: '8.1. Тестування компонентів' },
  content39: { component: Content39, title: '8.2. Тестування з використанням Jest' },
  content40: { component: Content40, title: '8.3. End-to-end тестування' }
};

const contentKeys = Object.keys(contentMap);
const isOpenArray = ref(Array(contentKeys.length).fill(false));

// Для темної теми
const isDarkTheme = ref(false);

const toggleOpen = (index) => {
  isOpenArray.value[index] = !isOpenArray.value[index];
}

// Перемикач теми
const toggleTheme = () => {
  isDarkTheme.value = !isDarkTheme.value;
}
</script>

<template>
  <div :class="{ 'dark-theme': !isDarkTheme, 'white-theme': isDarkTheme }">
    <button @click="toggleTheme">
      {{ !isDarkTheme ? 'Світла тема' : 'Темна тема' }}
    </button>

    <!-- Генерація пунктів за допомогою v-for -->
    <div v-for="(key, index) in contentKeys" :key="index" class="content-section">
      <h2 @click="toggleOpen(index)" :class="{ 'open': isOpenArray[index] }">
        {{ contentMap[key].title }} ({{ isOpenArray[index] ? '-' : '+' }})
      </h2>

      <div v-if="isOpenArray[index]" class="content">
        <component :is="contentMap[key].component"/>
      </div>
    </div>
  </div>
</template>

<style scoped>
h2 {
  margin: 1rem 0;
  cursor: pointer;
  padding: 0.5rem 1rem;
  background-color: #42b883;
  color: #ffffff;
  border-radius: 5px;
  transition: background-color 0.3s, transform 0.3s;
}

h2:hover {
  background-color: #35495e;
  transform: scale(1.02);
}

h2.open {
  background-color: #35495e;
}

.content {
  padding: 3rem;
  margin: 0.5rem 0;
  background-color: #f9f9f9;
  border-left: 4px solid #42b883;
  border-radius: 5px;
  box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
}

.dark-theme {
  padding: 2rem;
  background-color: #121212;
  color: #ffffff;
}

.white-theme {
  padding: 2rem;

  background-color: #ffffff;
  color: rgba(9, 17, 21, 0.94);
}

.dark-theme h2 {
  background-color: #1f1f1f;
  color: #ffffff;
}

.dark-theme h2.open {
  background-color: #333;
}

.dark-theme .content {
  background-color: #2c2c2c;
  border-left-color: #666;
  box-shadow: 0 2px 10px rgba(0, 0, 0, 0.5);
}

button {
  margin-bottom: 1rem;
  padding: 0.5rem 1rem;
  cursor: pointer;
  background-color: #42b883;
  color: #fff;
  border: none;
  border-radius: 5px;
  transition: background-color 0.3s;
}

button:hover {
  background-color: #35495e;
}

.dark-theme button {
  background-color: #333;
}

.dark-theme button:hover {
  background-color: #555;
}
</style>
