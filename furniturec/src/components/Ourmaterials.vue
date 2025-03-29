<template>
    <div class="container">
      <h2 class="title">Our materials</h2>
      <div class="materials-container">
        <div class="material-item" v-for="item in materialItems" :key="item.name">
        
          <img :src="item.imageUrl" :alt="item.name" />
          <p>{{item.name}}</p>
          
        </div>
      </div>
    </div>
  </template>
  
  <script setup>

  // Vue 3 Composition API
  import { ref, computed } from 'vue';

// Import images
import matImg from '@/assets/mat.png';
import jacquardImg from '@/assets/jacquard.png';
import artificial_leatherImg from '@/assets/artificial_leather.png';
import classicImg from '@/assets/classic.png';
import microfiberImg from '@/assets/microfiber.png';
import VelourImg from '@/assets/Velour.png';
import Italian_leatherImg from '@/assets/Italian_leather.png';

  const materialItems = ref([
  { name:" Velour ", imageUrl: VelourImg , selected: false },
  { name: "Jacquard", imageUrl: jacquardImg , selected: false },
  { name: "Artificial leather" , imageUrl: artificial_leatherImg , selected: false },
  { name: "Classic", imageUrl: classicImg , selected: false },
  { name: "Microfiber" , imageUrl: microfiberImg , selected: false },
  { name:" Mat ", imageUrl: matImg , selected: false },
  { name : "Italian leather", imageUrl: Italian_leatherImg , selected: false }
]);


  </script>
  
  <style scoped>
  .container {
    width: 1184px;
    min-height: 496px;
    border: 1px solid black;
    margin: 50px auto;
    display: flex;
    flex-direction: column;
    align-items: center;
    padding: 30px 20px;
    box-sizing: border-box;
  }
  
  .title {
    width: 678px;
    height: 43px;
    font-size: 33px;
    /* margin: 0 0 40px 0; */
    text-align: center;
    font-weight:bold;
    }
  
  .materials-container {
    display: flex;
    justify-content: center;
    /* gap: 10px; */
    flex-wrap: nowrap;
    margin-top: 30px;
  }
  
  .material-item {
    width: 163px;
    height: 379px;
    border: 1px solid black;
    display: flex;
    justify-content: center;
    align-items: center;
    position: relative;
    & img{
      position:relative;
      z-index: 1;
    }
    & p{
      position:absolute;
      top: 10px;
      font-size: 23px;
      color: white;
      z-index: 2;
    }
  }

  /* Адаптация под смартфоны */
  @media (max-width: 480px) {
    .container {
      padding: 15px;
      width: 100%;
    }

    .title {
      font-size: 24px;
    }

    .materials-container {
      display: flex;
      flex-direction: column;
      align-items: center;
      gap: 15px;
    }

    .material-item {
      width: 100%; /* Элемент занимает всю ширину на маленьком экране */
      height: auto;
    }

    .material-item p {
      font-size: 16px;
    }
  }
  </style>