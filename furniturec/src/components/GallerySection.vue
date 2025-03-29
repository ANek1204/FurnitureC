<template>
    <div class="gallery">
      <div class="gallery-slider" :style="{ transform: `translateX(${currentSlide * -25}%)` }">
        <img 
          v-for="image in images" 
          :key="image.id"
          :src="image.src"
          :alt="image.alt"
          class="gallery-image"
        />
      </div>
      <div class="navigation">
        <button @click="prevSlide" :disabled="currentSlide === 0">❮</button>
        <button @click="nextSlide" :disabled="currentSlide === images.length - 1">❯</button>
      </div>
    </div>
  </template>
  
  <script setup>
  import { ref } from 'vue';
  
  const images = [
    { id: 1, src: '@/assets/sofa-repaired.jpg', alt: 'Ремонт дивана' },
    { id: 2, src: '@/assets/chair-restored.jpg', alt: 'Ремонт стула' },
    // Добавьте другие изображения...
  ];
  
  const currentSlide = ref(0);
  
  const nextSlide = () => {
    if (currentSlide.value < images.length - 1) {
      currentSlide.value++;
    }
  };
  
  const prevSlide = () => {
    if (currentSlide.value > 0) {
      currentSlide.value--;
    }
  };
  </script>
  
  <style scoped>
  .gallery {
    max-width: 1200px;
    margin: 0 auto;
    padding: 30px 0;
    position: relative;
  }
  
  .gallery-slider {
    display: flex;
    transition: transform 0.5s ease;
  }
  
  .gallery-image {
    width: 100%;
    height: auto;
    object-fit: cover;
    margin: 0 10px;
  }
  
  .navigation {
    display: flex;
    justify-content: center;
    gap: 20px;
    margin-top: 20px;
  }
  
  button {
    padding: 8px 16px;
    background-color: #4CAF50;
    color: white;
    border: none;
    cursor: pointer;
  }
  
  button:disabled {
    opacity: 0.5;
    cursor: not-allowed;
  }
  </style>