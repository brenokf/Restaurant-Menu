<script setup>
defineProps({
  product: {
    type: Object,
    required: true
  }
});

defineEmits(['add-to-cart']);
</script>

<template>
  <div class="product-card">
    <img :src="product.image" :alt="product.name" class="product-image">
    <div class="product-info">
      <h3 class="product-title">{{ product.name }}</h3>
      <p class="product-description">{{ product.description }}</p>
      <div class="product-footer">
        <div class="product-price">R$ {{ product.price.toFixed(2) }}</div>
        <button class="add-to-cart" @click.stop="$emit('add-to-cart', product)">
          <i class="fas fa-plus"></i>
        </button>
      </div>
    </div>
  </div>
</template>

<style scoped>
.product-card {
  background: var(--white);
  border-radius: 15px;
  overflow: hidden;
  box-shadow: 0 5px 15px rgba(0,0,0,0.08);
  transition: transform 0.3s ease, box-shadow 0.3s ease;
  cursor: pointer;
}

.product-card:hover {
  transform: translateY(-5px);
  box-shadow: 0 8px 25px rgba(0,0,0,0.12);
}

.product-image {
  height: 180px;
  width: 100%;
  object-fit: cover;
}

.product-info {
  padding: 20px;
}

.product-title {
  font-size: 1.2rem;
  font-weight: 600;
  margin-bottom: 8px;
  color: var(--primary-color);
}

.product-description {
  color: var(--text-light);
  font-size: 0.95rem;
  margin-bottom: 15px;
  line-height: 1.5;
  height: 60px;
  overflow: hidden;
}

.product-footer {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.product-price {
  font-size: 1.3rem;
  font-weight: 700;
  color: var(--secondary-color);
}

.add-to-cart {
  background: var(--secondary-color);
  color: var(--white);
  border: none;
  width: 40px;
  height: 40px;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  cursor: pointer;
  transition: var(--transition);
}

.add-to-cart:hover {
  background: #d35400;
  transform: scale(1.1);
}
</style>