<template>
    <div class="container">
      <h2 class="title">How we work</h2>
      
      <div class="image-container">
        <!-- Placeholder for the image -->
        <div class="main-image">
          <img src="@/assets/workman.png" alt="workman"  />     
        </div>
      </div>
      <div class="wrap-container">
      <div class="process-container">
        <div class="process-item" v-for="item in advantageItems" :key="item.name">
          <img :src="item.imageUrl" :alt="item.name" />
          <p>{{item.name}}</p>
        </div>
      
      </div>
      <button class="call-button">Call a surveyor</button>
     
    </div>
    </div>
  </template>
  
  <script setup>
  // Vue 3 Composition API
  import { ref, computed } from 'vue';

// Import images
import Advantage5Img from '@/assets/Advantage5.png';
import Advantage6Img from '@/assets/Advantage6.png';
import Advantage7Img from '@/assets/Advantage7.png';
import Advantage8Img from '@/assets/Advantage8.png';
import Advantage9Img from '@/assets/Advantage9.png';

  const advantageItems = ref([
  { name:" Calling a designer measurer with samples of materials", imageUrl: Advantage5Img , selected: false },
  { name:" Cost calculation and budgeting ", imageUrl: Advantage6Img , selected: false },
  { name:" Delivery of furniture to production ", imageUrl: Advantage7Img , selected: false },
  { name:" Furniture Restoration ", imageUrl: Advantage8Img , selected: false },
  { name:" Delivery of new furniture to your home ", imageUrl: Advantage9Img , selected: false },
  
]);

  </script>
  
  <style scoped>
  .container {
    width: 100%;
    max-width: 1023px;
    min-height: 462px;
    /* border: 1px solid black; */
    margin: 50px auto;
    display: flex;
    flex-direction: column;
    align-items: center;
    padding: 10px;
    box-sizing: border-box;
    position:relative;
  }
  
  .title {
    width: 678px;
    height: 43px;
    font-size: 33px;
    margin: 0 0 20px 0;
    text-align: center;
    font-weight: bold;
  }
  
  .image-container {
    min-width: 387px;
    min-height: 274px;
    /* margin-bottom: 20px; */
    position:relative;
    z-index: 20;
   
  }
  
  .main-image {
    width: 100%;
    height: 100%;
    /* border: 1px solid black; */
    display: flex;
    justify-content: center;
    align-items: center;
    /* background-color: #f0f0f0; */
   
  }
  .wrap-container{
    width: 100%;
    max-width: 1023px;
    min-height: 353px;
    border: 1px solid blue;
    box-shadow: 0px 4px 4px rgba(0, 0, 0, 0.25);
    display: flex;
    flex-direction: column;
    /* justify-content: center; */
    align-items: center;
    border-radius: 20px;
    padding: 50px 0px;
    z-index: 1;
    position:relative;
    top:-40px;
  }
  
  .process-container {
    width: 100%;
    max-width: 1023px;
    min-height: 174px;
    margin-bottom: 50px;
    display: flex;
    justify-content: space-around;
    align-items: center;
  }

    .process-item {
    width: 154px;
    min-height: 174px;
    display: flex;
    justify-content: center;
    align-items: center;
   
    position: relative;
    & img{
      position:relative;
      z-index: 1;
      padding-bottom: 50px;
      margin-bottom: 20px;
    }
    & p{
      position:absolute;
      bottom: 0px;
      font-size: 15px;
      line-height: 18px;
      color: black;
      z-index: 2;
      text-align: center;
    }
  }
  
  .call-button {
    width: 229px;
    height: 47px;
    background-color: blue;
    color: white;
    border: none;
    font-size: 16px;
    cursor: pointer;
     display: flex;
    justify-content: center;
    align-items: center; 
    margin: 0 auto 30px;
    border-radius: 10px;
  }

  @media (max-width: 768px) {
    .container, .wrap-container, .process-container {
    max-width: 100%;
    padding: 10px;
  }

    .title {
      width: auto;
      height: auto;
      font-size: 24px;
    }

    .wrap-container {
    
      top: -10px;
    }

    .process-container {
      flex-direction: column;
      gap: 20px; 
    }

    .process-item {
      width: 80%;
      min-height: auto;
    margin-bottom: 15px;
    }

    .call-button {
      font-size: 14px;
      height: 40px;
      margin-bottom: 50px;
    }
  }

  /* Адаптация под смартфоны */
  @media (max-width: 480px) {
    .container{
      width: 100%;
      margin: 30px auto;
    }
    .title {
      width: 100%;
      font-size: 14px;
    }
    .image-container {
    min-width: auto;
    width: 100%;
  }

  .main-image img {
    max-width: 100%;
    height: auto;
  }

    .wrap-container {
      min-height: auto;
      padding: 40px 10px 20px;
      /* padding: 10px;
      top: -10px; */
    }

    .process-container {
      min-height: auto;
      /* display: flex;
      justify-content: center;
      flex-wrap: wrap;
      flex-direction: column; */
    }

    .process-item {
      /* width: 80%; */
      width: 90%;
    display: flex;
    flex-direction: column;
    & img {
      max-width: 70px;
      padding-bottom: 30px;
    }
    & p {
      font-size: 14px;
      width: 100%;
      padding: 0 10px;
    }
    }

    .call-button {
      font-size: 14px;
      height: 40px;
    }
  }
  </style>