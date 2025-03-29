<template>
  <div class="wrap">
    <div class="santim">
    <img :src="imageSantim" alt="santim image" />
    </div>
    <div class="title">
    <h2>Calculate the preliminary cost of restoring your furniture</h2>
    </div>

  <div class="quiz-container">

    <div class="image-section">
      <img :src="imageSrc" alt="Quiz image" />
    </div>
    <div class="content-section">
      <div class="progress-bar">
        <div class="progress-fill" :style="{ width: progressWidth }"></div>
        <div class="progress-text" :style="{ color: getProgressTextColor }">Question {{ currentStep }} from 4</div>
      </div>
      
      <!-- Step 1: Furniture Type Selection -->
      <div v-if="currentStep === 1" class="question-section">
        <h2 class="question-title">Select furniture type</h2>
        <div class="furniture-grid">
          <div 
            v-for="(item, index) in furnitureItems" 
            :key="index" 
            class="furniture-item" 
            :class="{ 'selected': item.selected }"
            @click="toggleSelection(index)"
          >
            <span></span>
            {{item.name}}
             <p> </p>
            <img :src="item.imageUrl" :alt="item.name" />
          </div>
        </div>
      </div>
      
      <!-- Step 2: Furniture Parameters -->
<div v-if="currentStep === 2" class="question-section">
  <h2 class="question-title">Furniture parameters</h2>
  <div class="parameters-container">
    <div class="parameter-row" v-for="(param, index) in parameters" :key="index">
      <div class="parameter-name">{{ param.name }}</div>
      <div class="parameter-options">
        <div class="radio-column">
          <label class="radio-option">
            <input
              type="radio"
              :name="`param-${index}`"
              :value="0"
              v-model="param.selected"
            />
            <span class="radio-label">{{ param.lab0 }}</span>
          </label>
        </div>
        <div class="radio-column">
          <label class="radio-option">
            <input
              type="radio"
              :name="`param-${index}`"
              :value="1"
              v-model="param.selected"
            />
            <span class="radio-label">{{ param.lab1 }}</span>
          </label>
        </div>
        <div class="radio-column">
          <label class="radio-option">
            <input
              type="radio"
              :name="`param-${index}`"
              :value="2"
              v-model="param.selected"
            />
            <span class="radio-label">{{ param.lab2 }}</span>
          </label>
        </div>
      </div>
    </div>
  </div>
</div>
      
      <!-- Step 3: Furniture Materials -->
      <div v-if="currentStep === 3" class="question-section">
        <h2 class="question-title">Furniture materials</h2>
        <div class="materials-container">
          <div class="material-row">
            <div class="parameter-name">Material</div>
            <select class="material-select">
              <option value="classic">classic</option>
              <option value="modern">Modern</option>
              <option value="antic">Antic</option>
            </select>
          </div>
          <div class="material-row">
            <div class="parameter-name">Class</div>
            <div class="material-options">
              <label  class="radio-option">
                <input 
                  type="radio" 
                  :name="'class-option'" 
                  :value="optIndex" 
                  v-model="classSelected"
                />
                <span class="radio-label">Low (800 p/m)</span>
              </label>
              <label  class="radio-option">
                <input 
                  type="radio" 
                  :name="'class-option'" 
                  :value="optIndex" 
                  v-model="classSelected"
                />
                <span class="radio-label">Middle (800-1000 p/m)</span>
              </label>
              <label  class="radio-option">
                <input 
                  type="radio" 
                  :name="'class-option'" 
                  :value="optIndex" 
                  v-model="classSelected"
                />
                <span class="radio-label">Luxury (from 1000 p/m)</span>
              </label>
            </div>
          </div>
        </div>
      </div>
      
      <!-- Step 4: Price Information -->
      <div v-if="currentStep === 4" class="question-section">
        <h2 class="question-title">Price</h2>
        <div class="price-container">
          <!-- Three price boxes -->
          <div class="price-boxes">
            <div class="price-box" >
              <div class="price-text">Work from</div>
              <div class="price-text">R2000</div>
            </div>
            <div class="price-box" >
              <div class="price-text">Materials from </div>
              <div class="price-text">R2000</div>
            </div>
            <div class="price-box" >
              <div class="price-text">Total from</div>
              <div class="price-text">R4000</div>
            </div>


          </div>
          
          <!-- Place of order section -->
          <h3 class="sub-heading">Place of order</h3>
          
          <!-- Two test boxes -->
          <div class="order-boxes">
            <div class="order-box" >
              Name
            </div>
            <div class="order-box" >
              E-mail
            </div>

          </div>
        </div>
      </div>
      
      <div class="button-section">
        <button class="next-button" @click="nextStep">Next</button>
      </div>
    </div>
  </div>
</div>
</template>

<script setup>
import { ref, computed } from 'vue';
import bunLeftImage from '@/assets/bun-left.png';
import santimLeft from '@/assets/santim.png';  
// Import images
import sofaGrey from '@/assets/sofa_grey.png';
import armchair from '@/assets/sofa_armchair.png';
import chair from '@/assets/sofa_chair.png';
import bad from '@/assets/sofa_bad.png';
import sofaBrown from '@/assets/sofa_brown.png';
import sofaOther from '@/assets/sofa_chair_green.png';

// Using imported image reference
const imageSrc = ref(bunLeftImage);
const imageSantim = ref(santimLeft);

// Current step tracking
const currentStep = ref(1);
const maxSteps = 4;

// Compute progress width based on current step
const progressWidth = computed(() => {
  return `${(currentStep.value / maxSteps) * 100}%`;
});

// Новый computed для определения цвета текста в зависимости от прогресса
const getProgressTextColor = computed(() => {
  // Если прогресс больше 50%, используем белый цвет, иначе - черный
  return (currentStep.value / maxSteps) > 0.3 ? 'white' : '#333';
});

// Furniture items with selection state (Step 1)
const furnitureItems = ref([
  { name:" Sofa ", imageUrl: sofaGrey , selected: false },
  { name: "Armchair", imageUrl: armchair , selected: false },
  { name: "Chair" , imageUrl: chair , selected: false },
  { name: "Bad", imageUrl: bad , selected: false },
  { name: "Sofa corner" , imageUrl: sofaBrown , selected: false },
  { name : "Other", imageUrl: sofaOther , selected: false }
]);

// Toggle selection state for furniture items
const toggleSelection = (index) => {
  furnitureItems.value[index].selected = !furnitureItems.value[index].selected;
};

// Parameters for Step 2
const parameters = ref([
  { name: 'Furniture dimensions ', lab0: "Small 2 seater", lab1:" Medium 2-3 seater",  lab2: "Large 4-5 seater"  ,   selected: null },
  { name: 'Splendor of furniture', lab0: "No",             lab1: "Medium ",            lab2: "Splendor",             selected: null },
  { name: 'Replacing the filler ', lab0: "Тot required",   lab1: "Зartial restoration",lab2: "Сomplete replacement", selected: null }
]);

// Step 3 - Class selection
const classSelected = ref(null);

// Next step function
const nextStep = () => {
  if (currentStep.value < maxSteps) {
    currentStep.value++;
  } else {
    // Reset to first step if we've completed all steps
    currentStep.value = 1;
  }
};
</script>

<style scoped>
.quiz-container {
  position: absolute;
  left: 125px;
  top: 150px;
  width: 1023px;
  height: 481px;
  border: 1px solid black;
  display: flex;
  overflow: hidden;
  margin: 50px auto;
  border-radius: 20px;
}
.wrap{

  width: 1200px;
  height: 666px;
  margin : 50px auto;
  position: relative;
}

.image-section {
  width: 268px;
  height: 480px;
  overflow: hidden;
}

.image-section img {
  width: 100%;
  height: 100%;
  object-fit: cover;
}

.content-section {
  flex: 1;
  display: flex;
  flex-direction: column;
  padding: 0 20px;
}

.progress-bar {
  width: 569px;
  height: 30px;
  border: 1px solid #ddd;
  position: relative;
  /* margin-top: 20px;
  margin-bottom: 20px; */
  display: flex;
  align-items: center;
  justify-content: center;
  margin: 20px auto;
  
}

.progress-fill {
  position: absolute;
  left: 0;
  top: 0;
  height: 100%;
  background-color: blue;
  transition: width 0.3s ease;
  
}

.progress-text {
  position: relative;
  z-index: 1;
  font-size: 16px;
  mix-blend-mode: difference; /* Это делает текст контрастным */
  transition: color 0.3s ease; /* Плавный переход между цветами */
  left: -70px;
  
}

/* .question-section {
  flex: 1;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
} */

/* .question-title {
  text-align: center;
  margin-bottom: 30px;
} */

/* Step 1 styles */
.furniture-grid {
  display: grid;
  grid-template-columns: repeat(3, 180px);
  grid-template-rows: repeat(2, 56px);
  gap: 20px;
  justify-content: center;
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

.furniture-item.selected {
  background-color: blue;
  color: white;
}

/* Step 2 styles */

.question-section {
  margin: 20px 0;
  width: 100%;
}

.question-title {
  font-size: 24px;
  margin-bottom: 20px;  
  font-weight: bold;
  /*  */
   font-size: 24px;
  margin-bottom: 20px;  
  font-weight: bold;
  text-align: center;
  display: flex;
  justify-content: center;
  width: 100%;
}

.parameters-container {
  width: 100%;
}

.parameter-row {
  display: flex;
  margin-bottom: 20px;
  align-items: flex-start;
}

.parameter-name {
  width: 200px;
  font-weight: 500;
  padding-top: 5px;
}

.parameter-options {
  display: flex;
  flex: 1;
}

.radio-column {
  width: 33.33%;
  padding-right: 15px;
}

.radio-option {
  display: flex;
  align-items: center;
  cursor: pointer;
  margin-bottom: 5px;
}

.radio-option input[type="radio"] {
  margin-right: 8px;
}

.radio-label {
  font-size: 14px;
}


/* Step 3 styles */
.materials-container {
  width: 100%;
  max-width: 500px;
  margin: 0 auto;
}

.material-row {
  display: flex;
  margin-bottom: 20px;
  align-items: center;
  
}

.material-select {
  width: 256px;
  height: 42px;
  padding: 0 10px;
  font-size: 16px;
}
.material-options{
  display: flex;
  /* justify-content: space-between; */
  /* width: 250px; */
  & input {
    width: 100px;
  }
}


/* Step 4 styles */
.price-container {
  width: 100%;
  display: flex;
  flex-direction: column;
  align-items: center;
}

.price-boxes {
  display: flex;
  gap: 20px;
  justify-content: center;
  margin-bottom: 30px;
}

.price-box {
  border: 1px solid black;
  padding: 10px 15px;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}

.price-text {
  text-align: center;
}

.sub-heading {
  margin: 10px 0 20px;
  text-align: center;
}

.order-boxes {
  display: flex;
  gap: 20px;
  justify-content: center;
}

.order-box {
  width: 229px;
  height: 51px;
  border: 1px solid black;
  display: flex;
  align-items: center;
  justify-content: center;
}

.button-section {
  display: flex;
  justify-content: center;
  margin-bottom: 20px;
}

.next-button {
  width: 229px;
  height: 48px;
  background-color: blue;
  color: white;
  border: none;
  font-size: 16px;
  cursor: pointer;
}
.title{
  width:732px;
  height: 84px;
  font-size: 33px;
  font-weight: bold;
  line-height: 38px;
  margin: 30px auto;
  text-align: center;
  color: black;
}
.santim{
  position: absolute;
  top: 10px;
  left: -50px;
  
}

/* Медиа-запросы для адаптивности */

/* Планшеты */
@media (max-width: 1200px) {
  .wrap {
    width: 100%;
    height: auto;
    margin: 30px auto;
  }
  
  .quiz-container {
    position: relative;
    left: 0;
    top: 0;
    width: 90%;
    height: auto;
    margin: 0 auto;
    flex-direction: column;
  }
  
  .image-section {
    width: 100%;
    height: 200px;
  }
  
  .progress-bar {
    width: 90%;
    max-width: 569px;
  }
  
  .title {
    width: 90%;
    height: auto;
    font-size: 28px;
    line-height: 34px;
  }
  
  .furniture-grid {
    grid-template-columns: repeat(2, 180px);
    grid-template-rows: repeat(3, 56px);
  }
}

/* Мобильные устройства */
@media (max-width: 768px) {
  .quiz-container {
    width: 95%;
    border-radius: 15px;
  }
  
  .content-section {
    padding: 0 15px;
  }
  
  .progress-bar {
    height: 25px;
  }
  
  .progress-text {
    font-size: 14px;
    left: -30px;
  }
  
  .title {
    font-size: 24px;
    line-height: 30px;
    margin: 30px auto;
  }
  
  .question-title {
    font-size: 20px;
  }
  
  .furniture-grid {
    grid-template-columns: repeat(1, minmax(200px, 80%));
    gap: 15px;
  }
  
  .furniture-item {
    width: 100%;
    font-size: 16px;
  }
  
  .parameter-row {
    flex-direction: column;
  }
  
  .parameter-name {
    width: 100%;
    margin-bottom: 10px;
  }
  
  .parameter-options {
    width: 100%;
  }
  
  .material-row {
    flex-direction: column;
    align-items: flex-start;
  }
  
  .material-select {
    width: 100%;
    margin-bottom: 10px;
  }
  
  .material-options {
    width: 100%;
    justify-content: space-between;
  }
  
  .price-boxes {
    flex-direction: column;
    width: 100%;
  }
  
  .price-box {
    width: 100%;
  }
  
  .order-boxes {
    flex-direction: column;
    width: 100%;
    gap: 10px;
  }
  
  .order-box {
    width: 100%;
  }
  
  .next-button {
    width: 90%;
  }
  
  .santim {
    position: static;
    display: block;
    margin-bottom: 10px;
    margin-left: 0;
  }
}

/* Маленькие мобильные устройства */
@media (max-width: 480px) {
  .quiz-container {
    border-radius: 10px;
  }
  
  .image-section {
    height: 150px;
  }
  
  .progress-bar {
    height: 20px;
  }
  
  .progress-text {
    font-size: 12px;
    left: 0;
  }
  
  .title {
    font-size: 22px;
    line-height: 28px;
  }
  
  .question-title {
    font-size: 18px;
  }
  
  .furniture-item {
    height: 45px;
    font-size: 14px;
  }
  
  .radio-column {
    width: 100%;
    margin-bottom: 10px;
  }
  
  .parameter-options {
    flex-direction: column;
  }
  
  .radio-label {
    font-size: 12px;
  }
  
  .material-select {
    height: 36px;
    font-size: 14px;
  }
  
  .next-button {
    height: 40px;
    font-size: 14px;
  }
}

</style>