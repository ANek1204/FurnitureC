<script setup>
import { ref } from 'vue';
// Импортируем компонент Header
// import HeaderComponent from './components/HeaderComponent.vue';
import FloatingButton from './components/FloatingButton.vue';
import ServiceCard from './components/ServiceCard.vue';
import HeroSection from './components/HeroSection.vue'; // Импортируем компонент
import ServicesSection from './components/ServicesSection.vue';
import GallerySection from './components/GallerySection.vue';
import ContactForm from './components/ContactForm.vue';
import FooterComponent from './components/FooterComponent.vue';
import Service from './components/Service.vue';
import Calculator from './components/Calculator.vue';
import AboutUs from './components/AboutUs.vue';
import Disane from './components/Disane.vue';
import FAQ from './components/FAQ.vue';
import Ourworks from './components/Ourworks.vue';
import Ouroffers from './components/Ouroffers.vue';
import Ourmaterials from './components/Ourmaterials.vue';
import Surveyor from './components/Surveyor.vue';
import Reviews from './components/Reviews.vue';

// Создаём реактивную переменную
const clickCount = ref(0);

// Функция для увеличения счётчика
const incrementCounter = () => {
clickCount.value++;
};

</script>

<template>
  
    <div id="app">
      <!-- Шапка -->
     
      <!-- <HeaderComponent /> -->
     
      <br/>
      <HeroSection /> <!-- Добавляем HeroSection в начало -->
      <Service/>
      <Calculator id="calculatiion"/>
     
       <AboutUs id="about"/>
    
       <Ourworks id="galery"/>
       <Ouroffers/>
       <Disane/>
       <Ourmaterials/>
       <Surveyor id="contact"/>
       <Reviews id="reviews"/>
       <FAQ/>


   
 <!-- Плавающая кнопка -->
 <!-- <FloatingButton /> -->
    <FooterComponent />
    </div>
   
  </template>
  
 
  
  <style scoped>
  /* Общие стили для всего приложения */
  body {
    margin: 0;
    font-family: Arial, sans-serif;
    background-color: #F0D5B6;
  }

  .info {
    max-width: 1440px;
    display: flex;
    flex-direction: column;
  }

  /* Стили для мобильных устройств */
  @media (max-width: 768px) {
    .info {
      max-width: 100%; /* Увеличить область отображения для маленьких экранов */
      padding: 10px; /* Добавить отступы */
      flex-direction: column; /* Убедиться, что направление остается вертикальным */
    }

    body {
      font-size: 14px; /* Уменьшить размер текста для удобства чтения на маленьких экранах */
    }
  }

  @media (max-width: 480px) {
    .info {
      padding: 5px; /* Еще больше уменьшить отступы для очень маленьких экранов */
    }

    body {
      font-size: 12px; /* Еще меньше текст для компактных устройств */
    }
  }
</style>
