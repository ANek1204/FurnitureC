<template>
    <header class="header">
      <div class="container">
        <h1>Мастерская мебели</h1>
        <nav>
          <a href="#services">Услуги</a>
          <a href="#contact">Контакты</a>
        </nav>
      </div>
    </header>
  </template>
  
  <script setup>
  // Здесь пока ничего не нужно — компонент пустой!
  </script>
  
  <style scoped>
  .header {
    
    background-color: #333;
    color: white;
    padding: 20px 0;
  }
  
  .container {
    max-width: 1440px;
    margin: 0 auto;
    padding: 0 20px;
  }
  
  nav a {
    color: white;
    margin-left: 20px;
    text-decoration: none;
  }
  </style>