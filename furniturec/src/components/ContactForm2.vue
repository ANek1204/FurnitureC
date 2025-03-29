<template>
  <section class="contact-section">
    <h2>Оставьте заявку</h2>
    <form @submit.prevent="submitForm">
      <div class="form-group">
        <label for="name">Ваше имя:</label>
        <input 
          type="text" 
          id="name" 
          v-model="name" 
          required 
          :class="{ error: submitted && !name }"
        >
        <span v-if="submitted && !name" class="error-message">Обязательное поле</span>
      </div>

      <div class="form-group">
        <label for="phone">Телефон:</label>
        <input 
          type="tel" 
          id="phone" 
          v-model="phone" 
          required 
          :class="{ error: submitted && !phone }"
        >
        <span v-if="submitted && !phone" class="error-message">Обязательное поле</span>
      </div>

      <button type="submit" :disabled="isSubmitting">Отправить</button>
    </form>
    <div v-if="isSuccess" class="success-message">Заявка отправлена! Спасибо.</div>
  </section>
</template>

<script setup>
import { ref } from 'vue';

const name = ref('');
const phone = ref('');
const submitted = ref(false);
const isSubmitting = ref(false);
const isSuccess = ref(false);

const submitForm = async () => {
  submitted.value = true;

  if (!name.value || !phone.value) return;

  isSubmitting.value = true;
  try {
    // Мок отправки данных (замените на реальный API)
    await new Promise(resolve => setTimeout(resolve, 1500));
    isSuccess.value = true;
    resetForm();
  } finally {
    isSubmitting.value = false;
  }
};

const resetForm = () => {
  name.value = '';
  phone.value = '';
  submitted.value = false;
};
</script>

<style scoped>
.contact-section {
  padding: 50px 0;
  background-color: #f0f8ff;
}

.form-group {
  margin-bottom: 20px;
}

.error {
  border-color: #ff4444;
}

.error-message {
  color: #ff4444;
  font-size: 0.9em;
  margin-top: 5px;
}

.success-message {
  color: #4CAF50;
  font-weight: bold;
  margin-top: 20px;
}
</style>