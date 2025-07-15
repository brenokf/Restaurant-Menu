<script setup>
import { ref, computed } from 'vue';
import Header from './components/Header.vue';
import Banner from './components/Banner.vue';
import Categories from './components/Categories.vue';
import ProductList from './components/ProductList.vue';
import Footer from './components/Footer.vue';
import ShoppingCart from './components/ShoppingCart.vue';
import { categories } from './data/products.js';

const activeCategory = ref('all');
const cart = ref([]);
const cartOpen = ref(false);

const setActiveCategory = (categoryId) => {
  activeCategory.value = categoryId;
};

const openCart = () => {
  cartOpen.value = true;
};

const closeCart = () => {
  cartOpen.value = false;
};

const addToCart = (product) => {
  const existingItem = cart.value.find(item => item.id === product.id);
  
  if (existingItem) {
    existingItem.quantity++;
  } else {
    cart.value.push({
      ...product,
      quantity: 1
    });
  }
};

const updateQuantity = (item, change) => {
  const newQuantity = item.quantity + change;
  
  if (newQuantity > 0) {
    item.quantity = newQuantity;
  } else {
    removeFromCart(item);
  }
};

const removeFromCart = (item) => {
  cart.value = cart.value.filter(cartItem => cartItem.id !== item.id);
};

const cartItemCount = computed(() => {
  return cart.value.reduce((total, item) => total + item.quantity, 0);
});

const cartTotal = computed(() => {
  return cart.value.reduce((total, item) => total + (item.price * item.quantity), 0);
});
</script>

<template>
  <div id="app">
    <div class="app-container">
      <Header :cartItemCount="cartItemCount" @open-cart="openCart" />
      <Banner />
      <Categories :activeCategory="activeCategory" @set-category="setActiveCategory" />
      <ProductList :activeCategory="activeCategory" @add-to-cart="addToCart" />
      <Footer />
    </div>
    <ShoppingCart 
      :open="cartOpen" 
      :cart="cart" 
      :cartTotal="cartTotal"
      @close-cart="closeCart"
      @update-quantity="updateQuantity"
      @remove-item="removeFromCart"
    />
  </div>
</template>