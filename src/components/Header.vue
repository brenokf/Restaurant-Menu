<script setup>
defineProps({
  cartItemCount: {
    type: Number,
    required: true
  }
});

defineEmits(['open-cart']);
</script>

<template>
  <header class="header">
    <div class="header-content">
      <div class="logo">
        <i class="fas fa-utensils"></i>
        Sabor Elegante
      </div>
      <div class="cart-icon" @click="$emit('open-cart')">
        <i class="fas fa-shopping-cart fa-lg"></i>
        <span class="cart-count" :class="{ pulse: cartItemCount > 0 }">{{ cartItemCount }}</span>
      </div>
    </div>
  </header>
</template>

<style scoped>
.header {
  background: var(--primary-color);
  color: var(--white);
  padding: 20px 15px;
  position: sticky;
  top: 0;
  z-index: 100;
  box-shadow: var(--shadow);
}

.header-content {
  display: flex;
  justify-content: space-between;
  align-items: center;
  max-width: 1200px;
  margin: 0 auto;
}

.logo {
  font-size: 1.8rem;
  font-weight: 700;
  display: flex;
  align-items: center;
}

.logo i {
  margin-right: 10px;
  color: var(--secondary-color);
}

.cart-icon {
  position: relative;
  cursor: pointer;
}

.cart-count {
  position: absolute;
  top: -8px;
  right: -8px;
  background: var(--danger-color);
  color: var(--white);
  border-radius: 50%;
  width: 22px;
  height: 22px;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 0.75rem;
  font-weight: 600;
}

@media (max-width: 480px) {
  .header {
    padding: 15px 10px;
  }
  
  .logo {
    font-size: 1.5rem;
  }
}
</style>