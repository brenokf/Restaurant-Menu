<template>
  <div class="banner">
    <div class="banner-content">
      <h1>Menu Digital</h1>
      <p>Descubra nossas delícias gastronômicas preparadas com ingredientes frescos e selecionados</p>
    </div>
  </div>
</template>

<style scoped>
.banner {
  background: linear-gradient(rgba(0,0,0,0.6), rgba(0,0,0,0.6)), url('https://images.unsplash.com/photo-1517248135467-4c7edcad34c4?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1470&q=80');
  background-size: cover;
  background-position: center;
  height: 200px;
  display: flex;
  align-items: center;
  justify-content: center;
  color: var(--white);
  text-align: center;
  padding: 0 20px;
}

.banner h1 {
  font-size: 2.2rem;
  font-weight: 700;
  margin-bottom: 10px;
  text-shadow: 0 2px 4px rgba(0,0,0,0.5);
}

.banner p {
  font-size: 1.1rem;
  max-width: 600px;
  opacity: 0.9;
}

@media (max-width: 768px) {
  .banner h1 {
    font-size: 1.8rem;
  }
  
  .banner p {
    font-size: 1rem;
  }
}

@media (max-width: 480px) {
  .banner {
    height: 180px;
  }
}
</style>