<template>
    <div class="form-container">
      <h2>Want to know the cost?</h2>
      
      <div class="form-group">
        <label for="name">` </label>
        <input type="text" id="name" v-model="name" placeholder="Enter your name">
      </div>
      
      <div class="form-group">
        <label for="email">` </label>
        <input type="email" id="email" v-model="email" placeholder="Enter your email">
      </div>
      
      <button type="submit" @click="submitForm">Find out the cost</button>
    </div>
  </template>
  
  <script setup>
  import { ref } from 'vue';
  
  const name = ref('');
  const email = ref('');
  
  const submitForm = () => {
    console.log('Отправленные данные:', {
      name: name.value,
      email: email.value
    });
    
    // Здесь можно добавить логику отправки данных на сервер
    // Например, с помощью fetch или axios
    
    // Сброс формы после отправки
    name.value = '';
    email.value = '';
  };
  </script>
  
  <style scoped>
  .form-container {
    width: 357px;
    height: 405px;
    background-color: white;
    /* border-radius: 8px; */
    box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
    padding: 20px;
    box-sizing: border-box;
    display: flex;
    flex-direction: column;
    margin: 0 auto;
    border-radius: 15px;
    & h2{
      font-size: 27px;
      font-weight: 700;
    }
  }
  
  h2 {
    text-align: center;
    margin-bottom: 30px;
    color: #333;
  
  }
  
  .form-group {
    margin-bottom: 25px;
    display: flex;
    flex-direction: column;
  }
  
  label {
    margin-bottom: 8px;
    font-weight: bold;
    color: #555;
  }
  
  input {
    padding: 12px;
    border: 1px solid #ddd;
    border-radius: 8px;
    font-size: 16px;
  }
  
  input:focus {
    outline: none;
    border-color: #4a90e2;
    box-shadow: 0 0 5px rgba(74, 144, 226, 0.3);
  }
  
  button {
    background-color: #4a90e2;
    color: white;
    border: none;
    padding: 14px;
    border-radius: 8px;
    font-size: 16px;
    cursor: pointer;
    font-weight: bold;
    margin-top: auto;
  }
  
  button:hover {
    background-color: #3a80d2;
  }


  /* Адаптация под мобильные устройства */
  @media (max-width: 768px) {
    .form-container {
      width: 90%; /* Увеличить ширину для маленьких экранов */
      height: auto; /* Дать контейнеру адаптивную высоту */
      padding: 15px;
    }

    h2 {
      font-size: 24px; /* Уменьшить размер заголовка */
      margin-bottom: 20px;
    }

    input {
      padding: 10px;
      font-size: 14px; /* Уменьшить шрифт для полей ввода */
    }

    button {
      padding: 12px;
      font-size: 14px;
    }
  }

  @media (max-width: 480px) {
    .form-container {
      width: 95%; /* Почти полная ширина на очень маленьких экранах */
      padding: 10px;
    }

    h2 {
      font-size: 20px; /* Ещё меньше заголовок */
    }

    input {
      padding: 8px;
      font-size: 12px; /* Уменьшить шрифт и высоту полей */
    }

    button {
      padding: 10px;
      font-size: 12px; /* Подогнать кнопку под компактный дизайн */
    }
  }
  </style>