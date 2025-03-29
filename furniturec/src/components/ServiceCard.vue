<script setup>
  defineProps({
    title: String,
    description: String,
    imageSrc: String
  });
  </script>


<template>
    <div class="service-card">
      <img :src="imageSrc" :alt="title" class="service-icon" />
      <h3>{{ title }}</h3>
      <p>{{ description }}</p>
      <button class="learn-more">Узнать подробнее</button>
    </div>
  </template>
  
  
  
  <style scoped>
  .service-card {
    border: 1px solid #e0e0e0;
    padding: 20px;
    border-radius: 8px;
    transition: transform 0.2s;
  }
  
  .service-card:hover {
    transform: translateY(-5px);
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
  }
  
  .service-icon {
    width: 60px;
    height: 60px;
    margin-bottom: 15px;
  }
  </style>