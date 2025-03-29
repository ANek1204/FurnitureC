<template>
    <div class="main-container">
      <div class="title-section">
        <h2>We are in numbers</h2>
      </div>
      <div class="boxes-section">
        <div class="box" v-for="(item,index) in boxItems" :key="index">
          <!-- <span></span> -->
          <img :src="item.imageUrl" :alt="item.name" />
           <p> </p>
             {{item.name}}  
        </div>
      </div>
    </div>
  </template>
  
  <script setup>
  // Composition API не требует дополнительных импортов для базового компонента
  import { ref, computed } from 'vue';

// Import images
import group81 from '@/assets/Group 81.png';
import group85 from '@/assets/Group 85.png';
import group86 from '@/assets/Group 86.png';
import group88 from '@/assets/Group 88.png';
import group91 from '@/assets/Group 91.png';
import group84 from '@/assets/Group 84.png';


  const boxItems = ref([
  { name: "11 years of continuous work ", imageUrl: group81 , selected: false },
  { name: "Masters with more than 5 years of experience", imageUrl: group85 , selected: false },
  { name: "Three production workshops with a total area of ​​400 m2" , imageUrl: group86 , selected: false },
  { name: "6 days - average order fulfillment time", imageUrl: group84 , selected: false },
  { name: "Более 5000 выполненных заказов" , imageUrl: group88 , selected: false },
  { name: "Save up to 70% on the cost of new furniture", imageUrl: group91 , selected: false }
]);
  </script>
  
  <style scoped>
  .main-container {
    width: 1148px;
    min-height: 348px;
    border: 1px solid black;
    display: flex;
    flex-direction: column;
    margin: 50px auto;
  }
  
  .title-section {
    display: flex;
    justify-content: center;
    align-items: center;
    height: 70px; /* Примерная высота для верхней части */
    & h2{
      font-weight: bold;
      font-size: 33px;
    }
    
  }
  
  .boxes-section {
    flex: 1;
    display: flex;
    flex-wrap: wrap;
    justify-content: space-between;
    align-content: space-between;
    padding: 10px 10px 10px 0px;
    
  }
  
  .box {
    width: 365px;
    height: 92px;
    border: 1px solid #ccc;
    display: flex;
    justify-content: flex-start;
    align-items: center;
    margin-bottom: 10px;
    text-align: left;
    & span{
    padding-left: 10px;
    }
  
     & p{
    margin-right: 15px;
    } 
    & img {
      float: left
    }
  }
  .furniture-item {
  width: 180px;
  height: 56px;
  border: 3px solid #2c79FF;
  display: flex;
  align-items: center;
  justify-content: center;
  cursor: pointer;
  transition: background-color 0.3s;
  font-size: 19px;
  font-weight: bold;
  border-radius: 15px;
  line-height: 19px;
  & span{
    padding-left: 10px;
  }
  
  & p{
    margin-right: 15px;
 } 


}

 /* Mobile Responsive Breakpoints */
 @media screen and (max-width: 1200px) {
    .main-container {
      max-width: 95%;
    }
  }
  
  @media screen and (max-width: 992px) {
    .boxes-section {
      justify-content: space-around;
    }
    
    .box {
      width: 48%;
    }
    
    .furniture-item {
      width: 160px;
      font-size: 17px;
    }
  }
  
  @media screen and (max-width: 768px) {
    .box {
      width: 100%;
      height: auto;
      min-height: 80px;
      padding: 10px 0;
    }
    
    .furniture-item {
      width: 150px;
      height: 50px;
      font-size: 16px;
    }
  }
  
  @media screen and (max-width: 480px) {
    .main-container {
      margin: 10px auto;
    }
    
    .title-section {
      height: auto;
      min-height: 50px;
      padding: 10px;
    }
    
    .boxes-section {
      padding: 5px;
    }
    
    .box {
      margin-bottom: 8px;
    }
    
    .furniture-item {
      width: 130px;
      height: 45px;
      font-size: 14px;
      border-radius: 10px;
    }
  }
  </style>