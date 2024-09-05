<script setup>
import UserProfile from './UserProfile.vue';
import { ref } from "vue";

// Дані користувача
const user = ref({
  name: 'Олександр',
  age: 28,
  occupation: 'Програміст',
  avatar: 'https://img.icons8.com/ios-filled/100/000000/user-male-circle.png',
});

// Масив друзів користувача
const friends = ref(['Анна', 'Дмитро', 'Іван']);

// Статус онлайн
const isOnline = ref(true);

// Обробка події "Надіслати повідомлення"
const handleSendMessage = (message) => {
  alert(`Повідомлення відправлено: ${message}`);
};

// Обробка події "Додати друга"
const handleAddFriend = (newFriend) => {
  if (newFriend && !friends.value.includes(newFriend)) {
    friends.value.push(newFriend);
  }
};

// Зміна статусу онлайн
const toggleOnlineStatus = () => {
  isOnline.value = !isOnline.value;
};

// Оновлення даних користувача (редагування профілю)
const handleUpdateUser = (updatedUser) => {
  user.value = { ...user.value, ...updatedUser };
};
</script>

<template>
  <div>
    <h1>Профіль користувача</h1>
    <!-- Передаємо різні пропси в компонент профілю -->
    <UserProfile
        :user="user"
        :isOnline="isOnline"
        :friends="friends"
        @sendMessage="handleSendMessage"
        @addFriend="handleAddFriend"
        @toggleStatus="toggleOnlineStatus"
        @updateUser="handleUpdateUser"
    />
  </div>
</template>

<style scoped>
h1 {
  color: #2c3e50;
}
</style>
