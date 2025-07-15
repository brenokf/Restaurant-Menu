<script setup>
import { categories } from '../data/products.js';

defineProps({
  activeCategory: {
    type: String,
    required: true
  }
});

defineEmits(['set-category']);
</script>

<template>
  <div class="categories">
    <div 
      v-for="category in categories" 
      :key="category.id" 
      class="category" 
      :class="{ active: activeCategory === category.id }"
      @click="$emit('set-category', category.id)"
    >
      {{ category.name }}
    </div>
  </div>
</template>

<style scoped>
.categories {
  padding: 20px 15px;
  background: var(--white);
  overflow-x: auto;
  white-space: nowrap;
  scrollbar-width: none;
  position: sticky;
  top: 70px;
  z-index: 90;
  box-shadow: 0 4px 6px rgba(0,0,0,0.05);
}

.categories::-webkit-scrollbar {
  display: none;
}

.category {
  display: inline-block;
  padding: 10px 22px;
  margin: 0 8px;
  background: var(--bg-light);
  border-radius: 30px;
  font-weight: 500;
  cursor: pointer;
  transition: var(--transition);
}

.category.active {
  background: var(--secondary-color);
  color: var(--white);
}

@media (max-width: 480px) {
  .categories {
    padding: 15px 10px;
  }
  
  .category {
    padding: 8px 18px;
    font-size: 0.9rem;
  }
}
</style>