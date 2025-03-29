<template>
       <!-- Футер -->
        <!-- <img src="@/assets/Rectangle 35.png" alt="35" class="image"> -->
        <div class="container"> 
        
       <footer class="footer">
        <div class="info">
          <img src="@/assets/logo (5).png" alt="logo" class="image" />
        </div>
        © 2025   Furniture repairs
      </footer>
       </div>
</template>

<script setup>

import { ref } from 'vue'

const logoSrc = ref(('@/assets/logo11.jpg'))

</script>

<style scoped>
.container{
  margin: 30px auto;
}
.footer{
  position: relative;
  background-image: url("@/assets/Rectangle 35.png");
  background-size: cover;
  background-position: center;
  width: 1148px;
  height: 123px; /* Установите нужную высоту */
  display: flex;
  align-items: center;
  justify-content: center;
 color: white;
 margin: 0 auto;
} 
.info img {
  position: absolute;
  top: 25px;
  left: 134px;
  width: 120px;
  height: 60px;
  align-items: center;
}

/* Стили для мобильных устройств */
@media (max-width: 768px) {
  .footer {
    width: 100%; /* Ширина контейнера по размеру экрана */
    height: 100px; /* Уменьшаем высоту */
    flex-direction: column; /* Перестраиваем элементы в колонку */
    padding: 10px; /* Добавляем отступы */
  }
  
  .info img {
    top: 15px; /* Уменьшаем отступ сверху */
    left: 50px; /* Центрируем изображение для мобильных */
    width: 100px; /* Уменьшаем размер изображения */
    height: 50px; /* Уменьшаем высоту изображения */
  }
}

@media (max-width: 480px) {
  .footer {
    height: 80px; /* Еще меньше высота для компактных экранов */
    padding: 5px; /* Уменьшаем отступы */
  }
  
  .info img {
    top: 10px; /* Уменьшаем отступ сверху для еще меньших экранов */
    left: 20px; /* Центрируем изображение ближе к левому краю */
    width: 80px; /* Уменьшаем изображение еще сильнее */
    height: 40px; /* Подгоняем высоту изображения */
  }
}
</style>