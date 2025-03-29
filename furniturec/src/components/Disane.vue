
<template>
    <div class="container">
      <div class="content">
        <div class="left-section">
          <h2 class="main-title">Do you want to completely change the shape and design of your old furniture?</h2>
          <p class="subtitle">We are ready to do this based on your drawings, sketches, or photographs.</p>
          <div class="image-container">
            <!-- Placeholder for the image -->
            <div class="placeholder-image">
              <img src="@/assets/disane.png" alt="disane" class="image" />
             
            </div>
          </div>
        </div>
        <div class="ruler_stic">
          <img src="@/assets/ruler_stic.png" alt="ruler_stic"  />     
        </div>
        <div class="right-section">
         
          <div class="right-block">
       <ContactForm/>     
       
        </div>
        </div>
      
      </div>
    </div>
  </template>
  
  <script setup>
  // Vue 3 Composition API
  import ContactForm from './ContactForm.vue';
  </script>
  
  <style scoped>
  .container {
    width: 1181px;
    min-height: 544px;
    border: 1px solid black;
    margin: 50px auto;
    display: flex;
    align-items: center;
    padding: 20px;
    box-sizing: border-box;
    
  }
  
  .content {
    display: flex;
    width: 100%;
    height: 100%;
    justify-content: space-between;
  }
  
  .left-section {
    display: flex;
    flex-direction: column;
    align-items: flex-start;
  }
  
  .main-title {
    width: 772px;
    min-height: 84px;
    font-size: 33px;
    margin: 0 0 15px 0;
    line-height: 1.3;
    font-weight:bold;
  }
  
  .subtitle {
    width: 643px;
    height: 26px;
    font-size: 16px;
    margin: 0 0 20px 0;
  }
  
  .image-container {
    width: 592px;
    min-height: 335px;
  }
  
  .placeholder-image {
    width: 100%;
    height: 100%;
    background-color: #f0f0f0;
    display: flex;
    justify-content: center;
    align-items: center;
    border: 1px dashed #ccc;
  }
  
  .right-section {
    display: flex;
    /* align-items: center; */
    margin-top:50px;
    justify-content: center;
    position:relative;
    z-index: 98;
    background: white;
  
  }
  .ruler_stic {
    position:relative;
    z-index: 1;
  }
  .ruler_stic img {
    position: absolute;
    top: -60px;
    left: -80px;
   } 
  
  
  .right-block {
    width: 357px;
    height: 405px;
    /* border: 1px solid black; */
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
    border-radius: 20px;
    box-shadow: 10px 10px 5px rgba(0, 0, 0, 0.3);
    z-index: 99;

  }
  .input {
    width: 229px;
    height: 51px;
    border-radius: 10px;
    margin-bottom: 20px;
    margin: 10px auto;
 
    text-indent: 10px;
  }  

    /* Адаптация под планшеты */
    @media (max-width: 768px) {
    .container {
      width: 90%;
      height: auto;
      padding: 15px;
      flex-direction: column;
    }

    .content {
      flex-direction: column;
      gap: 20px;
    }

    .main-title {
      width: 100%;
      font-size: 28px;
      text-align: center;
    }

    .subtitle {
      width: 100%;
      font-size: 14px;
      text-align: center;
    }

    .image-container {
      width: 100%;
      height: auto;
    }

    .right-block {
      width: 100%;
      height: auto;
    }
  }

  /* Адаптация под смартфоны */
  @media (max-width: 480px) {
    .container {
      padding: 5px;
      margin-bottom: 10px;
    }

    .main-title {
      font-size: 24px;
      padding-bottom: 10px;
    }

    .subtitle {
      font-size: 12px;
      padding-bottom: 10px;
    }
    .image-container {
      width: 100%;
      height: auto;
      padding: 5px;
    }
    .image{
      margin-top:50px;
      width: 100%;
      height:100%;
    }
    .input {
      width: 100%;
      height: 45px;
    }
  }
  </style>