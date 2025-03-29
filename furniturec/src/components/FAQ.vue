<template>
    <div class="container">
      <h2 class="title">FAQ</h2>
      <div class="accordions-container">
        <div class="column">
          <div class="accordion" v-for="(item, index) in leftAccordions" :key="index">
            <div 
              class="accordion-header" 
              @click="toggleAccordion(index, 'left')"
            >
              {{ item.title }}
              <span class="accordion-icon">{{ item.isOpen ? '−' : '+' }}</span>
            </div>
            <div class="accordion-content" v-if="item.isOpen">
              {{ item.content }}
            </div>
          </div>
        </div>
        <div class="column">
          <div class="accordion" v-for="(item, index) in rightAccordions" :key="index">
            <div 
              class="accordion-header" 
              @click="toggleAccordion(index, 'right')"
            >
              {{ item.title }}
              <span class="accordion-icon">{{ item.isOpen ? '−' : '+' }}</span>
            </div>
            <div class="accordion-content" v-if="item.isOpen">
              {{ item.content }}
            </div>
          </div>
        </div>
      </div>
    </div>
  </template>
  
  <script setup>
  import { ref } from 'vue';
  
  // Create FAQ data
  const defaultContent = "Our company's specialists try to complete each order as quickly as possible. However, given the order statistics, the average time for completing one project is 5-10 days.";
  const defaultContent3 = "The price for furniture reupholstery or creating a new design varies based on several factors. These include the type of furniture, the complexity of the work, the chosen materials, and the dimensions of the piece. On average, reupholstering a chair might start around $150, an armchair from $300, and a sofa from $500. Creating a new design could increase the cost by 20-30% due to additional design and manufacturing efforts. To get an accurate estimate, it's best to consult with a specialist and provide photos of the furniture.";
  const defaultContent4 = "Yes, we work with custom designs. Our specialists will help you bring any ideas to life, from classic to the boldest and most modern. We are ready to create a unique design that emphasizes your style and individuality, taking into account all your wishes and preferences.";
 const defaultContent5 = "Yes, we do replace upholstery and filling of furniture even if you provide your own materials. We understand that some clients prefer to source their own fabrics or fillings for personal or specific reasons. In such cases, we are happy to work with your materials and ensure a professional and high-quality finish. However, we may need to inspect the materials beforehand to ensure they are suitable for the job and meet our quality standards. In any case, we are ready to work with any materials you provide.";
const defaultContent6 = "We offer several convenient payment options to make your order process smooth. You can pay by credit card, debit card, bank transfer, or through online payment platforms like PayPal. We also accept cash payments for in-person transactions. Please let us know which payment method you prefer, and we will provide you with the necessary details to complete your order.";
const defaultContent7 ="Yes, we do offer discounts for customers who provide multiple pieces of furniture for repair. The exact discount percentage will depend on the number of items and the scope of work involved. We value your patronage and are happy to provide a more cost-effective solution for larger projects. Please provide us with a list of the furniture you'd like to have repaired, and we'll be happy to provide you with a customized quote that includes any applicable discounts.";


  const leftAccordions = ref([
    { title: "Is it necessary to take my furniture away for repairs?", content:"Yes, because it is simply not possible to carry out professional repairs and furniture re-upholstery at home. To perform high-quality repairs and re-upholstery, professional stationary equipment is used, which is large in size and weight and which cannot be brought to the client's home.", isOpen: false },
    { title: "What is the order fulfillment period?", content: defaultContent, isOpen: false },
    { title: "What is the price for furniture reupholstery or creating a new design?", content: defaultContent3, isOpen: false },
    { title: "Do you work with custom designs?", content: defaultContent4, isOpen: false }
  ]);
  
  const rightAccordions = ref([
    { title: "Do you replace upholstery and filling of furniture if the material is mine?", content: defaultContent5, isOpen: false },
    { title: "How do I pay for my order?", content: defaultContent6, isOpen: false },
    { title: "If I give several pieces of furniture for repair, will there be a discount?", content: defaultContent7, isOpen: false }
  ]);
  
  // Function to toggle accordion state
  const toggleAccordion = (index, column) => {
    if (column === 'left') {
      leftAccordions.value[index].isOpen = !leftAccordions.value[index].isOpen;
    } else {
      rightAccordions.value[index].isOpen = !rightAccordions.value[index].isOpen;
    }
  };
  </script>
  
  <style scoped>
  .container {
    width: 1140px;
    min-height: 909px;
    border: 1px solid black;
    margin: 25px auto;
    padding: 30px;
    box-sizing: border-box;
  }
  
  .title {
    width: 678px;
    height: 43px;
    font-size: 33px;
    margin: 0 0 30px 20px;
    text-align: left;
    font-weight: bold;
  }
  
  .accordions-container {
    display: flex;
    justify-content: space-between;
  }
  
  .column {
    width: 560px;
    margin: 0 15px;
  }
  
  .accordion {
    margin-bottom: 15px;
    border: 1px solid #e0e0e0;
    border-radius: 4px;
  }
  
  .accordion-header {
    padding: 15px;
    background-color: #f5f5f5;
    cursor: pointer;
    display: flex;
    justify-content: space-between;
    align-items: center;
    font-weight: bold;
  }
  
  .accordion-icon {
    font-size: 18px;
    font-weight: bold;
  }
  
  .accordion-content {
    padding: 15px;
    border-top: 1px solid #e0e0e0;
    line-height: 1.5;
  }

/* Mobile adaptation */
@media (max-width: 768px) {
  .container {
    padding: 20px;
    margin: 15px auto;
  }

  .title {
    font-size: 24px;
    text-align: center;
  }

  .accordions-container {
    display: flex;
    flex-direction: column;
    gap: 10px;
  }

  .column {
    width: 100%;
  }

  .accordion-header {
    padding: 12px;
    font-size: 16px;
  }

  .accordion-content {
    padding: 12px;
    font-size: 14px;
  }
}

@media (max-width: 480px) {
  .container {
    padding: 10px;
    margin: 5px auto;
    width: 100%;
  }

  .title {
    font-size: 14px;
    text-align: center;
  }

  .accordions-container {
    display: flex;
    flex-direction: column;
    gap: 5px;
  }

  .column {
    width: 80%;
  }

  .accordion-header {
    padding: 5px;
    font-size: 16px;
  }

  .accordion-content {
    padding: 5px;
    font-size: 14px;
  }
}
  </style>