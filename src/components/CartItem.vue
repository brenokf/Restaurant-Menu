<script setup>
defineProps({
  item: {
    type: Object,
    required: true
  }
});

defineEmits(['update-quantity', 'remove-item']);
</script>

<template>
  <div class="cart-item">
    <img :src="item.image" :alt="item.name" class="cart-item-image">
    <div class="cart-item-details">
      <h4 class="cart-item-title">{{ item.name }}</h4>
      <div class="cart-item-price">R$ {{ (item.price * item.quantity).toFixed(2) }}</div>
      <div class="cart-item-actions">
        <button class="quantity-btn" @click="$emit('update-quantity', -1)">
          <i class="fas fa-minus"></i>
        </button>
        <span class="quantity">{{ item.quantity }}</span>
        <button class="quantity-btn" @click="$emit('update-quantity', 1)">
          <i class="fas fa-plus"></i>
        </button>
        <button class="remove-item" @click="$emit('remove-item')">
          <i class="fas fa-trash"></i>
        </button>
      </div>
    </div>
  </div>
</template>

<style scoped>
.cart-item {
  display: flex;
  padding: 15px 0;
  border-bottom: 1px solid #eee;
}

.cart-item-image {
  width: 80px;
  height: 80px;
  border-radius: 10px;
  object-fit: cover;
  margin-right: 15px;
}

.cart-item-details {
  flex: 1;
}

.cart-item-title {
  font-weight: 600;
  margin-bottom: 5px;
}

.cart-item-price {
  color: var(--secondary-color);
  font-weight: 600;
  margin-bottom: 10px;
}

.cart-item-actions {
  display: flex;
  align-items: center;
}

.quantity-btn {
  width: 30px;
  height: 30px;
  background: var(--bg-light);
  border: none;
  border-radius: 5px;
  display: flex;
  align-items: center;
  justify-content: center;
  cursor: pointer;
}

.quantity {
  margin: 0 10px;
  font-weight: 500;
}

.remove-item {
  margin-left: 15px;
  color: var(--danger-color);
  background: none;
  border: none;
  cursor: pointer;
}
</style>