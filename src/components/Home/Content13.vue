<template>
  <div>
    <h1>Стан підключення: {{ isConnected ? 'Підключено' : 'Відключено' }}</h1>
  </div>
</template>

<script>
import { ref, watchEffect, onUnmounted } from 'vue';

export default {
  setup() {
    const isConnected = ref(false);

    // Імітація підключення через WebSocket або подібне з'єднання
    const connect = () => {
      console.log('Підключення до сервера...');
      isConnected.value = true;
    };

    const disconnect = () => {
      console.log('Відключення від сервера...');
      isConnected.value = false;
    };

    // Спостерігач, який слідкує за підключенням
    const stopWatcher = watchEffect((onCleanup) => {
      connect(); // Відбувається підключення при активації спостерігача

      // Чистка підписки через onCleanup
      onCleanup(() => {
        console.log('Чистка підписки через onCleanup');
        disconnect(); // Викликається при очищенні ресурсу
      });
    });

    // Додатково, можемо викликати очищення під час unmounted компонента
    onUnmounted(() => {
      stopWatcher(); // Очищаємо спостерігач при демонтованому компоненті
    });

    return {
      isConnected,
    };
  },
};
</script>
