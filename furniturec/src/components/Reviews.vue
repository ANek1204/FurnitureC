<template>
  <div class="container">
    <div class="hummer">
      <img src="@/assets/pngwing5.png" alt="pngwing" class="image" />
    </div>
    <h2 class="title">Reviews</h2>
   
    <div class="reviews-container">
      <button class="carousel-btn prev" @click="prevSlide" :disabled="currentIndex <= 0">❮</button>
      
      <div class="carousel">
        <div class="carousel-track" :style="{ transform: `translateX(-${currentIndex * slideWidth}px)` }">
          <div class="review-item" v-for="(review, index) in reviews" :key="review.id">
            <div class="review-image">
              {{ review.name }} <br/>
              {{ review.year }} <br/>
              {{ review.content }}
            </div>
          </div>
        </div>
      </div>
      
      <button class="carousel-btn next" @click="nextSlide" :disabled="currentIndex >= reviews.length - slidesToShow">❯</button>
    </div>
    
    <div class="carousel-dots">
      <span 
        v-for="(_, index) in Math.ceil(reviews.length / slidesToShow)" 
        :key="index" 
        :class="['dot', {'active': Math.floor(currentIndex / slidesToShow) === index}]"
        @click="goToSlide(index * slidesToShow)">
      </span>
    </div>
  </div>
</template>

<script setup>
// Vue 3 Composition API
import { ref, computed } from 'vue';

// Sample review data - replace with your actual data
const reviews = ref([
  { id: 1, name: "Jonathan Edward Thompson", year: "2 years ago",   content: "I recently had my old sofa repaired, and I'm absolutely thrilled with the results. The team was professional, efficient, and incredibly skilled. They transformed my worn-out sofa into a piece that looks brand new. The quality of the workmanship is outstanding, and the new upholstery is both beautiful and durable. I appreciate their attention to detail and their commitment to customer satisfaction. I highly recommend their services to anyone looking to breathe new life into their furniture. They exceeded my expectations in every way. Thank you for a job well done!" },
  { id: 2, name: "Elizabeth Anne Williams", year: "3 years ago",  content: "I am writing to express my utmost satisfaction with the recent repair of my armchair. The craftsmanship and attention to detail were truly remarkable. The chair looks and feels like new, and I am incredibly pleased with the results. The team was professional, courteous, and efficient, completing the work in a timely manner. I highly recommend their services to anyone seeking quality furniture repair. The service was prompt and professional, and the price was very reasonable.Thank you for your excellent work!" },
  { id: 3, name: "Alexander James Blackwood", year: "2 years ago",  content: "I recently had a dining chair repaired, and I'm very pleased with the outcome. The craftsmanship was excellent, and the chair looks as good as new. The team was professional and efficient, completing the repair quickly. The new upholstery is of high quality and matches the other chairs perfectly. I appreciate their attention to detail and friendly service. I would definitely recommend their services for furniture repair. Thank you for restoring my chair!" },
  { id: 4, name: "Victoria Margaret Harrison", year: "3 years ago",  content: "I recently had my bed repaired, and I couldn't be happier with the service. The team was professional, efficient, and incredibly skilled. They transformed my old, sagging bed into a sturdy and comfortable piece of furniture. The craftsmanship was top-notch, and the new upholstery is both beautiful and durable. I appreciate their attention to detail and their commitment to customer satisfaction. They exceeded my expectations in every way. Thank you for a job well done!"  },
  { id: 5, name: "Christopher Michael Pemberton", year: "4 years ago",  content: "I had a wobbly old stool that I thought was beyond repair. But this team worked wonders! They tightened the legs, replaced the worn-out seat, and gave it a fresh coat of varnish. Now it's sturdy and looks fantastic. I'm so impressed with their skill and attention to detail. They even matched the new seat to the original color. I highly recommend them for any furniture repair needs. They're reliable, affordable, and do excellent work. My stool is like new again!" },
  { id: 6, name: "Olivia Charlotte Huntington", year: "5 years ago",  content: "I had an old bedside table that was falling apart, and I decided to have it repaired. I'm so glad I did! The team did an amazing job. They fixed the broken drawers, replaced the damaged veneer, and even polished the surface to a beautiful shine. The table looks brand new! I was impressed with their attention to detail and their commitment to quality. The service was prompt and professional, and the price was very reasonable. I highly recommend them for any furniture repair needs. They truly brought my old table back to life!" }
]);

const currentIndex = ref(0);
const slidesToShow = ref(2); // Number of slides to show at once
const slideWidth = 410; // Width of each slide including margin

// Carousel navigation functions
const nextSlide = () => {
  if (currentIndex.value < reviews.value.length - slidesToShow.value) {
    currentIndex.value++;
  }
};

const prevSlide = () => {
  if (currentIndex.value > 0) {
    currentIndex.value--;
  }
};

const goToSlide = (index) => {
  currentIndex.value = index;
};
</script>

<style scoped>
.container {
  width: 950px;
  height: 469px;
  border: 1px solid black;
  margin: 50px auto;
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 0 20px 20px 20px;
  box-sizing: border-box;
  position:relative;
}
.hummer{
position:absolute;
top: -90px;
right: -200px;
z-index: 2;
}
.title {
  width: 678px;
  height: 43px;
  font-size: 33px;
  margin: 0 0 20px 0;
  text-align: center;
  font-weight: bold;
}

.reviews-container {
  display: flex;
  justify-content: center;
  align-items: center;
  gap: 15px;
  position: relative;
  width: 100%;
}

.carousel {
  width: 820px;
  overflow: hidden;
  position: relative;
}

.carousel-track {
  display: flex;
  transition: transform 0.5s ease;
  width: 100%;
}

.review-item {
  width: 390px;
  height: 397px;
  flex-shrink: 0;
  margin: 0 10px;
  box-sizing: border-box;
  /* padding: 20px; */
}

.review-image {
  width: 100%;
  min-height: 100%;
  border: 1px solid black;
  display: flex;
  justify-content: center;
  align-items: center;
  background-color: #f0f0f0;
  font-size: 18px;
  box-sizing: border-box;
  padding: 10px;
}

.carousel-btn {
  background: rgba(0, 0, 0, 0.5);
  color: white;
  border: none;
  border-radius: 50%;
  width: 30px;
  height: 30px;
  font-size: 18px;
  cursor: pointer;
  display: flex;
  align-items: center;
  justify-content: center;
  z-index: 10;
  flex-shrink: 0;
}

.carousel-btn:disabled {
  opacity: 0.3;
  cursor: not-allowed;
}

.carousel-dots {
  display: flex;
  justify-content: center;
  margin-top: 30px;
  
}

.dot {
  height: 10px;
  width: 10px;
  background-color: #bbb;
  border-radius: 50%;
  display: inline-block;
  margin: 0 5px;
  cursor: pointer;
}

.dot.active {
  background-color: #333;
}

/* Адаптация для мобильных */
@media (max-width: 768px) {
  .container {
    padding: 0 10px;
    margin: 20px auto;
  }

  .title {
    font-size: 24px;
    width: 100%;
  }

  .reviews-container {
    flex-direction: column;
    gap: 10px;
  }

  .carousel {
    width: 100%;
  }

  .review-item {
    width: 90%;
    margin: 0 auto;
  }

  .review-image {
    font-size: 14px;
    min-height: 150px;
  }

  .carousel-btn {
    width: 25px;
    height: 25px;
    font-size: 16px;
  }

  .dot {
    height: 8px;
    width: 8px;
  }
}

/* Адаптация под смартфоны */
@media (max-width: 480px) {
  .container {
    padding: 0 10px;
    margin: 10px auto;
    width: 100%;

  }

  .title {
    font-size: 14px;
    width: 100%;
  }

  .reviews-container {
    flex-direction: column;
    gap: 10px;
  }

  .carousel {
    width: 100%;
  }

  .review-item {
    width: 90%;
    margin: 0 auto;
  }

  .review-image {
    font-size: 14px;
    min-height: 70px;
  }

  .carousel-btn {
    width: 15px;
    height: 15px;
    font-size: 8px;
  }

  .dot {
    height: 6px;
    width: 6px;
  }
  }

</style>