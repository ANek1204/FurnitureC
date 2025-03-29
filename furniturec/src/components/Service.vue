<script setup>
import ContactForm from './ContactForm.vue';
</script>

<template>
    <div class="wrap">
  <div class="container-service">

    <div class="service-subtext">
      <h3>We will restore the original appearance of old furniture, saving up to 70% of your budget</h3>
    </div>
     <div class="service-info">
        <div class="info-left">
       <div class="block">
        <img src="@/assets/Group 83.png" alt="furniture repair" title="furniture repair">
       </div>
       <div class="block">
        <img src="@/assets/Group 70.png" alt="furniture repair" title="furniture repair">
       </div>
       <div class="block">
        <img src="@/assets/Group 80.png" alt="furniture repair" title="furniture repair">
       </div>
       </div>
       <div class="info-fight">
       <div class="block">
        <img src="@/assets/Group 79.png" alt="furniture repair" title="furniture repair">
       </div>
       <div class="block">
        <img src="@/assets/Group 10.png" alt="furniture repair" title="furniture repair">
       </div>
       <div class="block">
        <img src="@/assets/Group 69.png" alt="furniture repair" title="furniture repair">
       </div>
       </div>

     </div>
  
   </div>

   <div class="form-win">
  <ContactForm/>
</div> 
  </div>



</template>

<style scoped>
.wrap{
    display: flex;
    justify-content: center;
    align-items: top;
    margin: 50px auto;
}
.container-service{
   
width: 740px;
height: 450px;
border: 1px solid black;

/* margin-left: 140px; */
}
.service-subtext {
  width: 740px;  
  height: 87px;
  font: OpenSans;
  font-size: 32px;
  line-height: 38px;
  text-align: left;
  color: black;
  /* font-weight: bold; */
  white-space: wrap;
  margin-bottom: 20px;
  line-height: 43px; /* Creates good spacing for two lines */
  text-align: left; /* Centers the text, remove if not needed */
  font-weight: bold; /* Makes text stand out, remove if not needed */
  /* border: 1px solid black; */
  & h3{
    font-weight: 600;
  }

}

.form-win{
    width: 357px;
    height: 405px;
    border: 1px solid black;
    margin-left: 48px;
    display: flex;
    flex-direction: column;
    box-shadow: 10px 10px 5px rgba(0, 0, 0, 0.3);
    border-radius: 15px;
 
}

.input {
    width: 229px;
    height: 51px;
    border-radius: 10px;
    margin-bottom: 20px;
    margin: 10px auto;
 
    text-indent: 10px;
  }  

.block{

width: 344px;
height: 91.50px;
/* border: 1px solid black; */
margin-bottom: 20px;

 & img{
    width: 100%;
    height: 100%;
    /* object-fit: contain; */
    object-fit:fill; 
       
 }
}
.service-info{
    display: flex;
    justify-content: space-between;
    align-items: top;
}


/* Медиа-запросы для адаптивности */

/* Планшеты */
@media (max-width: 1024px) {
    .wrap {
        flex-direction: column;
        align-items: center;
        margin: 30px auto;
    }
    
    .container-service {
        width: 90%;
        height: auto;
        max-width: 720px;
    }
    
    .service-subtext {
        font-size: 28px;
        line-height: 36px;
        height: auto;
        margin-bottom: 20px;
    }
    
    .form-win {
        margin-left: 0;
        margin-top: 30px;
    }
    
    .service-info {
        flex-direction: column;
    }
    
    .block {
        width: 100%;
        max-width: 344px;
        margin: 0 auto 20px;
    }
}

/* Мобильные устройства */
@media (max-width: 768px) {
    .wrap {
        margin: 20px auto;
    }
    
    .container-service {
        width: 95%;
    }
    
    .service-subtext {
        font-size: 24px;
        line-height: 32px;
    }
    
    .form-win {
        width: 95%;
        max-width: 357px;
        height: auto;
        min-height: 405px;
        padding: 15px 0;
    }
    
    .input {
        width: 80%;
        height: 45px;
    }
    
    .block {
        width: 95%;
        height: auto;
        aspect-ratio: 344/91.5;
    }
}

/* Маленькие мобильные устройства */
@media (max-width: 480px) {
    .service-subtext {
        font-size: 22px;
        line-height: 28px;
    }
    
    .form-win {
        box-shadow: 5px 5px 3px rgba(0, 0, 0, 0.3);
    }
    
    .input {
        height: 40px;
    }
}

</style>