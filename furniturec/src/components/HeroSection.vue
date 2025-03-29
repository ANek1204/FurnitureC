<template>
  <section class="hero">
    <div class="wrapper">
      <div class="root">
        <div class="info">
          <img src="@/assets/logo (5).png" alt="logo" class="image" />
        </div>

        <!-- Гамбургер-меню для мобильных устройств -->
        <div class="hamburger-menu" @click="toggleMenu">
          <div :class="['bar', { active: isMenuOpen }]"></div>
          <div :class="['bar', { active: isMenuOpen }]"></div>
          <div :class="['bar', { active: isMenuOpen }]"></div>
        </div>

        <!-- Навигационное меню -->
        <div :class="['nav-menu', { open: isMenuOpen }]">
          <ul class="list">
            <li><a href="#about" @click="navigateTo('about')">About us</a></li>
            <li>
              <a href="#calculatiion" @click="navigateTo('calculation')"
                >Price calculation</a
              >
            </li>
            <li><a href="#galery" @click="navigateTo('galery')">Gallery</a></li>
            <li>
              <a href="#reviews" @click="navigateTo('reviews')">Reviews</a>
            </li>
            <li>
              <a href="#contact" @click="navigateTo('contact')">Contact Us</a>
            </li>
          </ul>
        </div>
      </div>
    </div>

    <div class="hero-content">
      <h1>Furniture repair and re-upholstery</h1>
      <p>
        We will restore the original appearance of old furniture, saving your
        budget
      </p>
      <div class="hero-pic">
        <div class="benefit-item">
          <img src="@/assets/price.png" alt="" />
          <p class="hero-text">Lowest prices</p>
        </div>
        <div class="benefit-item">
          <img src="@/assets/roll.png" alt="" />
          <p class="hero-text">Quality materials</p>
        </div>
      </div>

      <button class="hero-button">Price calculation</button>
    </div>
    <img src="@/assets/main.jpg" alt="Ремонт мебели" class="hero-image" />
  </section>
</template>

<script setup>
import { ref } from "vue";

// Состояние меню (открыто/закрыто)
const isMenuOpen = ref(false);

// Функция для плавного скролла
const scrollTo = (id) => {
  const element = document.getElementById(id);
  if (element) {
    element.scrollIntoView({ behavior: "smooth" });
  }
};

// Функция для переключения меню
const toggleMenu = () => {
  isMenuOpen.value = !isMenuOpen.value;
  // Блокировка прокрутки страницы при открытом меню
  document.body.style.overflow = isMenuOpen.value ? "hidden" : "";
};

// Функция для навигации и закрытия меню
const navigateTo = (id) => {
  scrollTo(id);
  isMenuOpen.value = false;
  document.body.style.overflow = "";
};
</script>

<style scoped>
.hero {
  position: relative;
  height: 970px;
  margin-bottom: 50px;
  width: 1440px; /* Set fixed width instead of max-width */
  border: 1px solid black;
  margin-left: auto;
  margin-right: auto;
  overflow: hidden;
  /* This prevents the image from extending outside the hero container */
}


.wrapper {
    width: 100%;
  } 

.hero-image {
  width: 100%; /* Takes full width of parent (which is 1440px) */
  height: 100%;
  object-fit: cover;
  position: absolute;
  top: 0;
  left: 0;
  z-index: -1;
}


.hero-content {
    position: absolute;
    top: 546px;
    left: 500px;
    transform: translate(-50%, -50%);
    
   text-align: center;
    color: white;
    z-index: 1;
  } 


.hero-content h1 {
    font-family: "Open Sans", sans-serif;
    font-size: 62px;
    font-weight: bold;
    width: 678px;
    height: 119px;
    line-height: 72px;
    margin-bottom: 52px;
    text-align: left;
    color: black;
  } 

.hero-content p {
    font-size: 18px;
    margin-bottom: 30px;
    width: 460px;
    height: 66px;
    line-height: 36px;
    color: black;
    text-align: left;
  } 

.hero-button {
    color: white;
    border: none;
    border-radius: 5px;
    cursor: pointer;
    transition: all 0.3s;
    background-color: #1d5cca;
    width: 229px;
    height: 51px;
    float: left;
    font-family: "Open Sans", sans-serif;
    font-size: 16px;
    line-height: 19px;
  }

.hero-button:hover {
  background-color: #2c79ff;
}

.hero-pic {
    display: flex;
    justify-content: start;
  
 margin-bottom: 50px; 
align-items: center;
}  
 .benefit-item {
    display: flex;
    justify-content: start;
    
  align-items: center;
    width: 200px;
    height: 64px;
    & p{
   margin-top: 50px;
   margin-left: 20px;
 } 
  } 

.hero-text {
    width: 114px;
    height: 24px;
    font-size: 16px !important;
    line-height: 19px !important;
    color: black;
    margin-top: 10px;
  }

.image {
  width: 50px;
  height: 50px;
  margin-right: 20px;
  padding: 10px;
}

.root {
    display: flex;
    background-color: #f29000;
    width: 100%;
    justify-content: space-between;
    align-items: center;
    position: relative;
    padding: 15px 30px;
    z-index: 1000;
  }

.info img {
  width: 120px;
  height: 60px;
}

.list {
    display: flex;
    font-family: "Open Sans", sans-serif;
    list-style: none;
    align-items: center;
    gap: 25px;
    margin: 0;
    padding: 0;
  }

li {
  margin-right: 50px;
  font-size: 16px;
}

li:hover {
  text-decoration: underline;
  cursor: pointer;
}

a {
  text-decoration: none;
  color: rgb(12, 11, 11);
  transition: 0.4s;
  padding: 3px;
}

@media (hover: hover) {
  a:hover {
    background-color: hsla(249, 100%, 37%, 0.075);
    border-radius: 5px;
  }
}

/* Стили для гамбургер-меню */
.hamburger-menu {
  display: none;
  flex-direction: column;
  justify-content: space-between;
  width: 30px;
  height: 21px;
  cursor: pointer;
  z-index: 1001;
}

.bar {
  height: 3px;
  width: 100%;
  background-color: #000;
  border-radius: 10px;
  transition: all 0.3s ease;
}

/* Анимация для гамбургер-меню */
.bar.active:nth-child(1) {
  transform: translateY(9px) rotate(45deg);
}

.bar.active:nth-child(2) {
  opacity: 0;
}

.bar.active:nth-child(3) {
  transform: translateY(-9px) rotate(-45deg);
}

/* Стили для мобильного меню */
.nav-menu {
  transition: all 0.3s ease;
}

/* Add this to maintain responsiveness while still having 1440px width when possible */
@media (max-width: 1440px) {
  .hero {
    width: 100%; /* On smaller screens, take full available width */
  }
  .hero-image {
    width: auto; /* Allow natural width */
    min-width: 100%; /* Ensure it covers the width */
    min-height: 100%; /* Ensure it covers the height */
    left: 50%; /* Center horizontally */
    transform: translateX(-50%); /* Center horizontally */
  }
}

/* Адаптация под мобильные устройства */
@media (max-width: 1024px) {
  .hero-content {
      top: 50%;
      left: 50%;
      transform: translate(-50%, -50%);
      width: 90%;
    }
  
  .hero-content h1 {
      width: 100%;
      font-size: 48px;
      line-height: 58px;
      text-align: center;
      height: auto;
    }
  
    .hero-content p {
      width: 100%;
      text-align: center;
      height: auto;
    }
  
    .hero-pic {
      width: 100%;
      justify-content: center;
      gap: 30px;
    }
  
    .hero-button {
      float: none;
      margin: 0 auto;
      display: block;
    }
}

@media (max-width: 768px) {
  .hero {
      min-height: 800px;
    }

  .info img {
       width: 100px; 
      height: 50px;
      position: static;  
       }

  /* Показываем гамбургер-меню */
  .hamburger-menu {
      display: flex;
    }

  /* Скрываем обычное меню */
  .nav-menu {
      position: fixed;
      top: 0;
      right: -100%;
      width: 70%;
      height: 100vh;
      background-color: #f29000;
      padding-top: 100px;
      transition: 0.4s;
      box-shadow: -5px 0 15px rgba(0, 0, 0, 0.2);
    }
  
    .nav-menu.open {
      right: 0;
    }
  
    .list {
      flex-direction: column;
      width: 30%;
      align-items: start;
    }
  
    .list li {
      margin: 0;
      padding: 15px 0;
      width: 100%;
      text-align: center;
      border-bottom: 1px solid rgba(0, 0, 0, 0.1);
    }
  
    .hero-content h1 {
      font-size: 36px;
      line-height: 44px;
      margin-bottom: 30px;
    }
  
    .hero-content p {
      font-size: 16px;
      line-height: 24px;
      margin-bottom: 20px;
    }
}

@media (max-width: 480px) {
  .hero {
    height: 600px; /* Shorter height for mobile */
  }
  
  .hero-image {
    /* These settings ensure the image stays centered on very small screens */
    width: auto;
    height: 100%;
    max-width: none;
    left: 50%;
    transform: translateX(-50%);
  }

  .hero-content h1 {
      font-size: 28px;
      line-height: 34px;
    }
  
    .hero-content p {
      font-size: 14px;
      line-height: 20px;
    }
  
    .hero-pic {
      flex-direction: column;
      height: auto;
      gap: 20px;
      margin-bottom: 30px;
    }
  
    .hero-text {
      margin: 5px 0 0 0;
    }
  
    .hero-button {
      width: 180px;
    }
  
    .nav-menu {
      width: 85%;
    }
}
</style>
