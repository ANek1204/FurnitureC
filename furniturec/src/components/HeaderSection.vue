<template>
    <header class="header">
      <div class="container">
        <div class="logo">
          <img :src="logoSrc" alt="Logo" />
        </div>
        <nav class="navigation">
          <ul>
            <li v-for="item in navItems" :key="item.id">
              <a :href="item.link">{{ item.text }}</a>
            </li>
          </ul>
        </nav>
      </div>
    </header>
  </template>
  
  <script setup>
  import { ref } from 'vue'
  
  const logoSrc = ref(require('@/assets/logo11.jpg'))

  const navItems = ref([
    { id: 1, text: 'Особенности', link: '#features' },
    { id: 2, text: 'О нас', link: '#about' },
    { id: 3, text: 'Отзывы', link: '#testimonials' },
    { id: 4, text: 'Контакты', link: '#contact' }
  ])
  </script>
  
  <style scoped>
  .header {
    padding: 20px 0;
    background-color: #ffffff;
    box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
  }
  
  .container {
    max-width: 1200px;
    margin: 0 auto;
    padding: 0 15px;
    display: flex;
    justify-content: space-between;
    align-items: center;
  }
  
  .logo img {
    height: 40px;
  }
  
  .navigation ul {
    display: flex;
    list-style: none;
    padding: 0;
    margin: 0;
  }
  
  .navigation li {
    margin-left: 30px;
  }
  
  .navigation a {
    text-decoration: none;
    color: #333;
    font-weight: 500;
    transition: color 0.3s;
  }
  
  .navigation a:hover {
    color: #42b883;
  }
  </style>