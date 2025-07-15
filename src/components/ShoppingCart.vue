<script setup>
import CartItem from './CartItem.vue';

defineProps({
  open: {
    type: Boolean,
    required: true
  },
  cart: {
    type: Array,
    required: true
  },
  cartTotal: {
    type: Number,
    required: true
  }
});

defineEmits(['close-cart', 'update-quantity', 'remove-item']);
</script>

<template>
  <div class="cart" :class="{ open }">
    <div class="cart-header">
      <h3>Seu Pedido ({{ cart.length }})</h3>
      <button class="close-cart" @click="$emit('close-cart')">
        <i class="fas fa-times"></i>
      </button>
    </div>
    
    <div class="cart-items">
      <div v-if="cart.length === 0" class="empty-cart-message">
        <p>Seu carrinho está vazio</p>
        <p>Adicione itens deliciosos!</p>
      </div>
      
      <CartItem 
        v-for="(item, index) in cart" 
        :key="index" 
        :item="item" 
        @update-quantity="$emit('update-quantity', item, $event)"
        @remove-item="$emit('remove-item', item)"
      />
    </div>
    
    <div class="cart-footer">
      <div class="cart-total">
        <span>Total:</span>
        <span>R$ {{ cartTotal.toFixed(2) }}</span>
      </div>
      <button class="checkout-btn" :disabled="cart.length === 0">Finalizar Pedido</button>
    </div>
  </div>
  
  <div class="overlay" :class="{ active: open }" @click="$emit('close-cart')"></div>
</template>

<style scoped>
.cart {
  position: fixed;
  top: 0;
  right: -400px;
  width: 100%;
  max-width: 380px;
  height: 100vh;
  background: var(--white);
  z-index: 200;
  box-shadow: -5px 0 15px rgba(0,0,0,0.1);
  transition: right 0.4s ease;
  display: flex;
  flex-direction: column;
}

.cart.open {
  right: 0;
}

.cart-header {
  padding: 20px;
  background: var(--primary-color);
  color: var(--white);
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.close-cart {
  background: none;
  border: none;
  color: var(--white);
  font-size: 1.5rem;
  cursor: pointer;
}

.cart-items {
  flex: 1;
  overflow-y: auto;
  padding: 20px;
}

.empty-cart-message {
  text-align: center;
  padding: 40px 0;
  color: var(--text-light);
}

.cart-footer {
  padding: 20px;
  border-top: 1px solid #eee;
  background: var(--white);
}

.cart-total {
  display: flex;
  justify-content: space-between;
  font-size: 1.3rem;
  font-weight: 700;
  margin-bottom: 20px;
}

.checkout-btn {
  width: 100%;
  padding: 15px;
  background: var(--accent-color);
  color: var(--white);
  border: none;
  border-radius: var(--border-radius);
  font-size: 1.1rem;
  font-weight: 600;
  cursor: pointer;
  transition: background 0.3s ease;
}

.checkout-btn:hover {
  background: #219653;
}

.checkout-btn:disabled {
  background: #95a5a6;
  cursor: not-allowed;
}

.overlay {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: rgba(0,0,0,0.5);
  z-index: 150;
  display: none;
}

.overlay.active {
  display: block;
}

@media (max-width: 768px) {
  .cart {
    max-width: 320px;
  }
}

@media (max-width: 480px) {
  .cart {
    max-width: 280px;
  }
}
</style>