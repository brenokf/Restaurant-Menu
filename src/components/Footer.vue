<template>
  <footer class="footer">
    <div class="footer-content">
      <h3>Restaurante Sabor Elegante</h3>
      <div class="contact-info">
        <div class="contact-item">
          <i class="fas fa-map-marker-alt"></i>
          <span>Av. Gastronômica, 123 - Centro</span>
        </div>
        <div class="contact-item">
          <i class="fas fa-phone"></i>
          <span>(11) 9999-8888</span>
        </div>
        <div class="contact-item">
          <i class="fas fa-clock"></i>
          <span>Seg-Sáb: 11h às 23h | Dom: 12h às 22h</span>
        </div>
      </div>
      <div class="social-links">
        <a href="#" class="social-link"><i class="fab fa-instagram"></i></a>
        <a href="#" class="social-link"><i class="fab fa-facebook"></i></a>
        <a href="#" class="social-link"><i class="fab fa-whatsapp"></i></a>
      </div>
      <p>&copy; 2023 Sabor Elegante. Todos os direitos reservados.</p>
    </div>
  </footer>
</template>

<style scoped>
.footer {
  background: var(--primary-color);
  color: #ecf0f1;
  padding: 30px 20px;
  text-align: center;
  margin-top: 40px;
}

.footer-content {
  max-width: 1200px;
  margin: 0 auto;
}

.contact-info {
  display: flex;
  justify-content: center;
  gap: 30px;
  margin: 20px 0;
  flex-wrap: wrap;
}

.contact-item {
  display: flex;
  align-items: center;
  gap: 8px;
}

.social-links {
  display: flex;
  justify-content: center;
  gap: 20px;
  margin: 20px 0;
}

.social-link {
  color: var(--white);
  font-size: 1.5rem;
  transition: color 0.3s ease;
}

.social-link:hover {
  color: var(--secondary-color);
}
</style>