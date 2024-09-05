<script setup>
import {ref, defineProps} from "vue";
// Оголошуємо пропси для отримання даних від батьківського компонента
const props = defineProps({
  user: {
    type: Object,
    required: true,
  },
  isOnline: {
    type: Boolean,
    default: false,
  },
  friends: {
    type: Array,
    required: true,
  },
});

// Визначаємо події для батьківського компонента
const emit = defineEmits(['sendMessage', 'addFriend', 'toggleStatus', 'updateUser']);

// Функція для надсилання повідомлення
const sendMessage = () => {
  const message = `Привіт, це повідомлення від ${props.user.name}!`;
  emit('sendMessage', message);
};

// Додавання нового друга
const newFriendName = ref(''); // Новий друг
const addFriend = () => {
  if (newFriendName.value) {
    emit('addFriend', newFriendName.value);
    newFriendName.value = ''; // Очищуємо поле після додавання
  }
};

// Зміна статусу онлайн
const toggleStatus = () => {
  emit('toggleStatus');
};

// Поля для редагування профілю
const editedName = ref(props.user.name);
const editedAge = ref(props.user.age);
const editedOccupation = ref(props.user.occupation);

// Функція для редагування профілю
const updateUser = () => {
  emit('updateUser', {
    name: editedName.value,
    age: editedAge.value,
    occupation: editedOccupation.value,
  });
};
</script>

<template>
  <div class="profile">
    <div class="profile-header">
      <img :src="props.user.avatar" alt="Avatar" class="avatar" />
      <div class="profile-info">
        <h2>{{ props.user.name }}</h2>
        <p>Вік: {{ props.user.age }}</p>
        <p>Професія: {{ props.user.occupation }}</p>
        <p class="status" :class="{ online: props.isOnline, offline: !props.isOnline }">
          Статус: {{ props.isOnline ? 'Онлайн' : 'Офлайн' }}
        </p>
        <button @click="toggleStatus">Змінити статус</button>
      </div>
    </div>

    <div class="friends">
      <h3>Друзі:</h3>
      <ul>
        <li v-for="(friend, index) in props.friends" :key="index">{{ friend }}</li>
      </ul>
      <input v-model="newFriendName" type="text" placeholder="Додати друга" />
      <button @click="addFriend">Додати</button>
    </div>

    <button @click="sendMessage">Відправити повідомлення</button>

    <div class="edit-profile">
      <h3>Редагувати профіль</h3>
      <input v-model="editedName" type="text" placeholder="Ім'я" />
      <input v-model="editedAge" type="number" placeholder="Вік" />
      <input v-model="editedOccupation" type="text" placeholder="Професія" />
      <button @click="updateUser">Зберегти зміни</button>
    </div>
  </div>
</template>

<style scoped>
.profile {
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 20px;
  border: 1px solid #ccc;
  border-radius: 10px;
  width: 300px;
  margin: 20px auto;
  background-color: #f9f9f9;
}

.profile-header {
  display: flex;
  align-items: center;
}

.avatar {
  width: 80px;
  height: 80px;
  border-radius: 50%;
  margin-right: 20px;
}

.profile-info {
  text-align: left;
}

.status {
  font-weight: bold;
  margin-top: 10px;
}

.online {
  color: green;
}

.offline {
  color: red;
}

.friends {
  margin-top: 20px;
}

button {
  margin-top: 10px;
  padding: 10px 20px;
  background-color: #007bff;
  color: white;
  border: none;
  border-radius: 5px;
  cursor: pointer;
}

button:hover {
  background-color: #0056b3;
}

.edit-profile {
  margin-top: 20px;
}

.edit-profile input {
  display: block;
  margin: 5px 0;
  padding: 5px;
  width: 100%;
  box-sizing: border-box;
}
</style>
