<template>
    <div class="container">
      <h2 class="title">Our offers</h2>
      <div class="content">
        <div class="left-block">
          <div class="left-content">
            <img src="@/assets/Group 71.png" alt="Replacement and restoration of filler" title= "Replacement and restoration of filler" class="Group71" />
            <img src="@/assets/wood.png" alt="wood" class="wood" />
            <p>Replacement and restoration of filler</p>
          </div>
        </div>
        <div class="middle-column">
          <div class="middle-block72">
            <img src="@/assets/Group 72.png" alt="Replacing the spring block" class="image" />
            <p> Replacing the spring block</p>
          </div>
          <div class="middle-block74">
           <img src="@/assets/Group 74.png" alt="Repairing the frame" class="image" />
            <p>Repairing the frame</p>
          </div>
        </div>
        <div class="right-column">
          <div class="right-block73">
            <img src="@/assets/Group 73.png" alt="Replacement and repair of the mechanism" class="image" />
            <p>Replacement and repair of the mechanism</p>
          </div>
          <div class="right-block75">
            <img src="@/assets/Group 75.png" alt="We replace the upholstery" class="image" />
            <p>We replace the upholstery</p>
          </div>
        </div>
      </div>
    </div>
  </template>
  
  <script setup>
  // Vue 3 Composition API
  </script>
  
  <style scoped>
  .container {
    width: 1178px;
    height: 554px;
    border: 1px solid black;
    display: flex;
    flex-direction: column;
    align-items: center;
    padding: 20px;
    box-sizing: border-box;
    margin: 50px auto;
  }
  
  .title {
    font-size: 30px;
    margin-bottom: 20px;
    text-align: center;
    margin-bottom: 20px;
    font-weight: bold;
  }
  
  .content {
    display: flex;
    gap: 20px;
    height: 418px;
    width: 100%;
    margin-top: 20px;
  }
  
  .left-block {
    width: 366px;
    height: 418px;
    border: 1px solid black;
  }
  
  .left-content {
    position:relative;
    width: 100%;
    height: 100%;
    display: flex;
    justify-content: center;
    align-items: center;
    & img {
      /* position:relative; */
      margin-left: 10px;
      margin-top: 9px;
     
    }
    & p{
      position:absolute;
      margin-top: 270px;
      font-size: 23px;
      line-height: 29px;
      color: black;
      width: 259px;
      height: 53px;
     
      text-align: center;
     
    }

  }
  
  .middle-column {
    display: flex;
    flex-direction: column;
    gap: 18px;
  
  }
  
  .middle-block72 {
    width: 360px;
    height: 200px;
    border: 1px solid black;
    display: flex;
    justify-content: center;
    align-items: center;
    & img{
      position:relative;
      margin-left: 15px;
      margin-bottom: 25px;
    }
    & p{
      position:absolute;
      margin-top: 150px;
      font-size: 23px;
      line-height: 29px;
      color: black;
      width: 359px;
      height: 53px;
     
      text-align: center;
     
    }
   
  }
  .middle-block74 {
    /* position: relative; */
    width: 360px;
    height: 200px;
    border: 1px solid black;
    display: flex;
    justify-content: center;
    align-items: center;
    & img{
      position: relative;
      margin-left: 15px;
      margin-top: 70px;
    }
    & p{
      position:absolute;
      margin-top: -120px;
      font-size: 23px;
      line-height: 29px;
      color: black;
      width: 259px;
      height: 53px;
      text-align: center;
     
    }
   
  }
  
  .right-column {
    display: flex;
    flex-direction: column;
    gap: 18px;
  }
  
  .right-block73 {
    width: 380px;
    height: 200px;
    border: 1px solid black;
    display: flex;
    justify-content: center;
    align-items: center;
    & img{
      position:relative;
      margin-left: 15px;
      margin-bottom: 35px;
    }
    & p{
      position:absolute;
      margin-top: 120px;
      font-size: 23px;
      line-height: 29px;
      color: black;
      width: 359px;
      height: 53px;
     
      text-align: center;
     
    }
  }
  .right-block75 {
    width: 380px;
    height: 200px;
    border: 1px solid black;
    display: flex;
    justify-content: center;
    align-items: center;
    & img{
      position:relative;
      margin-left: 15px;
      margin-top: 20px;
    }
    & p{
      position:absolute;
      margin-top: -120px;
      font-size: 23px;
      line-height: 29px;
      color: black;
      width: 359px;
      height: 53px;
     
      text-align: center;
     
    }
  }
 
  .wood{
    position: absolute;
    top: -80px;
    left: 20px;
  }

  /* Адаптация под мобильные устройства */
@media (max-width: 768px) {
  .container {
    width: 90%;
    height: auto;
    margin: 20px auto;
    padding: 15px;
  }

  .title {
    font-size: 24px;
  }

  .content {
    flex-direction: column;
    gap: 15px;
    height: auto;
  }

  .left-block,
  .middle-block72,
  .middle-block74,
  .right-block73,
  .right-block75 {
    width: 100%;
    height: auto;
  }

  .left-content img,
  .middle-block72 img,
  .middle-block74 img,
  .right-block73 img,
  .right-block75 img {
    margin: 0 auto;
  }

  .left-content p,
  .middle-block72 p,
  .middle-block74 p,
  .right-block73 p,
  .right-block75 p {
    font-size: 18px;
    width: 80%;
    margin: 10px auto;
  }
}

@media (max-width: 480px) {
  .container {
    padding: 10px;
  }

  .title {
    font-size: 20px;
    font-weight: bold;
  }

  .content {
    gap: 10px;
  }

  .left-content p,
  .middle-block72 p,
  .middle-block74 p,
  .right-block73 p,
  .right-block75 p {
    font-size: 16px;
  }
}
  </style>