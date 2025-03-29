<script setup>
import ServiceCard from './ServiceCard.vue';


const services = [
  {
    id: 1,
    title: 'Ремонт диванов',
    description: 'Восстановление механизмов, замена обивки.',
    imageSrc: '@/assets/sofa.png'
  },
  {
    id: 2,
    title: 'Ремонт стульев',
    description: 'Исправление ножек, замена тканей.',
    imageSrc: '@/assets/chair.png'
  },
  // Добавьте другие услуги...
];

</script>

<template>
  
  <section class="services" style="height: 1500px">
        <h3>Наши услуги:</h3>
        <div class="services-grid">
      <ServiceCard 
        v-for="service in services" 
        :key="service.id"
        :title="service.title"
        :description="service.description"
        :image-src="service.imageSrc"
      />
    </div>
        <!-- Другие услуги аналогично -->
      </section>

</template>

<style>

.services-section {
  padding: 50px 0;
  background-color: #f8f9fa;
}

.services-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: 20px;
  margin-top: 30px;
}

</style>