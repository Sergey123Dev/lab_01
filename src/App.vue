<script setup>
import { RouterView, RouterLink } from 'vue-router'
</script>

<template>
  <div class="layout">
    <!-- Ліве бокове меню -->
    <aside class="sidebar">
      <img src="https://vuejs.org/images/logo.png" alt="Vue.js" class="logo" />
      <h1 class="lecture-title">Лекція 1 - Vue.js</h1>

      <!-- Навігація -->
      <nav>
        <RouterLink to="/" class="menu-link">Приклади</RouterLink>
      </nav>
    </aside>

    <!-- Контент роута -->
    <main class="content">
      <RouterView />
    </main>
  </div>
</template>

<style scoped>
/* Макет сторінки */
.layout {
  display: flex;
  min-height: 100vh;
}

/* Ліва панель (меню) */
.sidebar {
  background-color: rgba(9, 17, 21, 0.94);
  color: white;
  width: 220px;
  padding: 2rem 1rem;
  display: flex;
  flex-direction: column;
  align-items: center;
  box-shadow: 2px 0 5px rgba(0, 0, 0, 0.1);
}

.logo {
  width: 80px;
  margin-bottom: 1.5rem;
}

.lecture-title {
  font-size: 1.4rem;
  text-align: center;
  margin-bottom: 2rem;
  font-weight: bold;
}

/* Навігація (меню) */
nav {
  width: 100%;
}

.menu-link {
  display: block;
  padding: 1rem;
  text-align: center;
  color: white;
  text-decoration: none;
  border-radius: 5px;
  transition: background-color 0.3s ease;
}

.menu-link:hover {
  background-color: #35495e;
}

/* Контентна частина */
.content {
  flex-grow: 1;
  background-color: #f9f9f9;
}
</style>
