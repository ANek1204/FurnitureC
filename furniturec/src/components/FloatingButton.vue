<template>
    <button 
      class="floating-button" 
      :class="{ show: showButton }"
      @click="handleClick"
    >
    Oreder ({{ clickCount }}) <!-- Показываем счётчик -->
    </button>
  </template>
  
  <script setup>
  import { ref } from 'vue';
  
  // Рекативная переменная для отображения кнопки
  const showButton = ref(false);
  const clickCount = ref(0); // Новая реактивная переменная для счётчика кликов

  // Функция, которая активирует кнопку при скролле
  const handleScroll = () => {
    if (window.scrollY > 200) {
      showButton.value = true;
    } else {
      showButton.value = false;
    }
  };
  
  const handleClick = () => {
  clickCount.value++; // Увеличиваем счётчик при клике
  alert(`You order ${clickCount.value} time(s)!`);
};

  // Подписываемся на событие скролла
  window.addEventListener('scroll', handleScroll);
  
  // Очистка события при разрушении компонента (Vue 3)
  defineExpose({}); // Необязательно, но лучше добавить
  </script>
  
  <style scoped>
  .floating-button {
    position: fixed;
    right: 20px;
    bottom: 20px;
    padding: 15px 30px;
    background-color: #4CAF50;
    color: white;
    border: none;
    opacity: 0;
    /* transition: opacity 0.3s; */
    transition: opacity 0.3s ease, transform 0.3s ease;
    transform: translateY(50px);  /* Сдвигаем кнопку вниз */
  }
  
  .floating-button.show {
    opacity: 1; /* Кнопка становится видимой */
    transform: translateY(0); /*Возвращаем в исходное положение*/
  }
  </style>