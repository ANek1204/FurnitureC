<template>
  <div class="main-container">
    <div class="header-section">
      <h2 class="title">Our works</h2>
      <div class="furniture-catalog">
        <!-- Horizontal Menu -->
        <div class="menu-container">
          <div
            v-for="(category, index) in categories"
            :key="index"
            class="menu-item"
            :class="{ active: activeCategory === category.id }"
            @click="setActiveCategory(category.id)"
          >
            {{ category.name }}
          </div>
        </div>

        <!-- Gallery Section -->
        <div
          class="gallery-container"
          :class="{ expanded: activeCategory === 'allWorks' }"
        >
          <div
            v-for="(item, index) in filteredItems"
            :key="index"
            class="gallery-item"
          >
            <img
              :src="getImageUrl(item)"
              :alt="`${item.category} ${item.id}`"
              class="furniture-image"
              @error="handleImageError($event, item)"
            />
          
          </div>
        </div>
      </div>
    </div>
    <!-- <div class="works-section">
        <div class="work-item" v-for="index in 6" :key="index">
          Работа {{ index }}
        </div>
      </div> -->
  </div>
</template>

<script setup>
// Composition API component
import { ref, computed, watch } from "vue";


// Categories data
const categories = [
  { id: "sofas", name: "Sofas" },
  { id: "chairs", name: "Chairs" },
  { id: "beds", name: "Beds" },
  { id: "furnitureSet", name: "FurnitureSet" },
  { id: "allWorks", name: "AllWorks" },
];

// Active category state
const activeCategory = ref("sofas");

// Function to set active category
const setActiveCategory = (categoryId) => {
  activeCategory.value = categoryId;
};

// Generate items data
const generateItems = () => {
  const items = [];

  // Generate 6 items for each of the first 4 categories
  categories.slice(0, 4).forEach((category) => {
    for (let i = 1; i <= 6; i++) {
      items.push({
        id: i,
        category: category.id,
        // Store only the filename, not the full path
        imageName: `${category.id}${i}.png`,
        
      });
    }
  
  });
  console.log("items= ",items);
  return items;
};

const items = generateItems();


// Function to get image URL dynamically
const getImageUrl = (item) => {
  try {
    // Use Vite's import.meta.url approach for dynamic imports
    console.log(item);
    //  return new URL(`/src/assets/images/${item.imageName}`, import.meta.url)
    //    .href;
    return require(`@/assets/images/${item.imageName}`);
 
  } catch (error) {
    console.error("Error loading image:", error);
    return "";
  }
};

// Fallback for image loading errors
const handleImageError = (event, item) => {
  console.warn(`Failed to load image for ${item.category} ${item.id}`);
  event.target.src = "https://via.placeholder.com/360x238?text=Image+Not+Found";
};

// Filtered items based on active category
const filteredItems = computed(() => {
  if (activeCategory.value === "allWorks") {
    return items;
  } else {
    return items.filter((item) => item.category === activeCategory.value);
  }
});
// Calculate rows needed for current view
// const rowsNeeded = computed(() => {
//   const itemCount = filteredItems.value.length;
//   return Math.ceil(itemCount / 3); // 3 items per row
// });
</script>

<style scoped>
.main-container {
  width: 1184px;
  /* Удаляем фиксированную высоту, чтобы контейнер мог расширяться */
  min-height: 641px;
  border: 1px solid black;
  display: flex;
  flex-direction: column;
  margin: 50px auto;
}

.header-section {
  display: flex;
  flex-direction: column;
  align-items: center;
  padding-top: 10px;
  /* margin-bottom: 10px; */
}

.title {
  font-size: 33px;
  font-weight: bold;
  /* margin-bottom: 5px;
    margin-top: 0; */
}


.furniture-catalog {
  max-width: 1200px;
  margin: 0 auto;
  padding: 5px;
  width: 100%;
}

.menu-container {
  display: flex;
  justify-content: center;
  margin-bottom: 10px;
}

.menu-item {
  padding: 10px 20px;
  margin: 0 10px;
  cursor: pointer;
  font-size: 16px;
  transition: all 0.3s ease;
  font-weight: 700;
}

.menu-item:hover {
  color: #4a90e2;
}

.menu-item.active {
  color: #4a90e2;
  border-bottom: 2px solid #4a90e2;
}

/* Height for 2 rows (2 * 238px + gap) */
.gallery-container {
  display: flex;
  flex-wrap: wrap;
  justify-content: space-between;
  gap: 10px;
  transition: height 0.5s ease;
  /* min-height: 500px;  */
  /* overflow: hidden; */
  min-height: auto;
  height: auto;
  /* margin-bottom: auto; */
}

/* Height for 4 rows (4 * 238px + gaps) */
.gallery-container.expanded {
  height: auto;
  /* min-height: 1000px; 
  max-height: none; */
}

.gallery-item {
  width: 360px;
  height: 238px;
  margin-bottom: 20px;
}

.furniture-image {
  width: 100%;
  height: 100%;
  object-fit: cover;
  border: 1px solid #ddd;
  transition: transform 0.3s ease;
}
.furniture-image:hover {
  transform: scale(1.03);
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
}


.main-container {
  width: 1184px;
  min-height: 641px;
  border: 1px solid black;
  display: flex;
  flex-direction: column;
  margin: 50px auto;
}

.header-section {
  display: flex;
  flex-direction: column;
  align-items: center;
  padding-top: 10px;
}

.title {
  font-size: 33px;
}

.furniture-catalog {
  max-width: 1200px;
  margin: 0 auto;
  padding: 5px;
  width: 100%;
}

.menu-container {
  display: flex;
  justify-content: center;
  margin-bottom: 10px;
}

.menu-item {
  padding: 10px 20px;
  margin: 0 10px;
  cursor: pointer;
  font-size: 16px;
  transition: all 0.3s ease;
}

.menu-item:hover {
  color: #4a90e2;
}

.menu-item.active {
  color: #4a90e2;
  border-bottom: 2px solid #4a90e2;
}

.gallery-container {
  display: flex;
  flex-wrap: wrap;
  justify-content: space-between;
  gap: 10px;
  transition: height 0.5s ease;
  min-height: auto;
  height: auto;
}

.gallery-item {
  width: 360px;
  height: 238px;
  margin-bottom: 20px;
}

.furniture-image {
  width: 100%;
  height: 100%;
  object-fit: cover;
  border: 1px solid #ddd;
  transition: transform 0.3s ease;
}

.furniture-image:hover {
  transform: scale(1.03);
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
}

/* Адаптация под мобильные устройства */
@media (max-width: 768px) {
  .main-container {
    width: 90%; /* Уменьшаем ширину для планшетов */
    margin: 20px auto;
  }

  .title {
    font-size: 26px; /* Уменьшаем размер заголовка */
    text-align: center;
  }

  .menu-container {
    flex-direction: column;
    align-items: center;
  }

  .menu-item {
    font-size: 14px; /* Уменьшаем размер текста меню */
    margin: 5px 0;
    padding: 8px 15px;
  }

  .gallery-item {
    width: 100%; /* Галерея занимает всю ширину */
    height: auto;
  }
}

@media (max-width: 480px) {
  .main-container {
    width: 100%;
    padding: 10px;
  }

  .title {
    font-size: 22px; /* Ещё меньше размер текста для маленьких экранов */
  }

  .menu-container {
    flex-direction: column;
    align-items: flex-start;
  }

  .menu-item {
    font-size: 12px;
    padding: 5px 10px;
  }

  .gallery-item {
    width: 100%;
    height: auto;
    margin-bottom: 15px;
  }
}
</style>
