<script setup>
import ProductCard from './ProductCard.vue';
import { ref, computed } from 'vue';
import { products } from '../data/products.js';

const props = defineProps({
  activeCategory: {
    type: String,
    required: true
  }
});

const emit = defineEmits(['add-to-cart']);

const filteredProducts = computed(() => {
  if (props.activeCategory === 'all') {
    return products;
  }
  return products.filter(product => product.category === props.activeCategory);
});
</script>

<template>
  <div class="products">
    <h2 class="section-title">Destaques do Menu</h2>
    
    <div class="product-grid">
      <ProductCard 
        v-for="product in filteredProducts" 
        :key="product.id" 
        :product="product" 
        @add-to-cart="emit('add-to-cart', product)" 
      />
    </div>
  </div>
</template>

<style scoped>
.products {
  padding: 20px 15px;
  max-width: 1200px;
  margin: 0 auto;
}

.section-title {
  font-size: 1.6rem;
  margin-bottom: 20px;
  color: var(--primary-color);
  font-weight: 600;
  padding-bottom: 10px;
  border-bottom: 2px solid var(--secondary-color);
  display: inline-block;
}

.product-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
  gap: 25px;
  margin-top: 20px;
}

@media (max-width: 768px) {
  .product-grid {
    grid-template-columns: 1fr;
  }
  
  .section-title {
    font-size: 1.4rem;
  }
}

@media (max-width: 480px) {
  .products {
    padding: 15px 10px;
  }
}
</style>