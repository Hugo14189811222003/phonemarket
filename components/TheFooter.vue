<template>
  <footer class="site-footer">
    <div class="footer-top">
      <button @click="scrollToTop" class="back-to-top">
        Volver al inicio
      </button>
    </div>

    <div class="footer-middle">
      <div class="footer-container">
        <div class="footer-column">
          <h3>Conócenos</h3>
          <ul>
            <li><a href="#">Trabajar en MarketPhone</a></li>
            <li><a href="#">Información corporativa</a></li>
            <li><a href="#">Departamento de prensa</a></li>
            <li><a href="#">MarketPhone Science</a></li>
          </ul>
        </div>
        <div class="footer-column">
          <h3>Gana dinero con nosotros</h3>
          <ul>
            <li><a href="#">Vender en MarketPhone</a></li>
            <li><a href="#">Suministro para MarketPhone</a></li>
            <li><a href="#">Programa de afiliados</a></li>
            <li><a href="#">Anuncia tus productos</a></li>
          </ul>
        </div>
        <div class="footer-column">
          <h3>Métodos de pago</h3>
          <ul>
            <li><a href="#">Tarjetas de crédito y débito</a></li>
            <li><a href="#">Tarjetas de regalo</a></li>
            <li><a href="#">Meses sin intereses</a></li>
            <li><a href="#">MarketPhone Cash</a></li>
          </ul>
        </div>
        <div class="footer-column">
          <h3>Podemos ayudarte</h3>
          <ul>
            <li><a href="#">Rastrear pedido</a></li>
            <li><a href="#">Devoluciones y Reemplazos</a></li>
            <li><a href="#">Gestión de contenido y dispositivos</a></li>
            <li><a href="#">Ayuda</a></li>
          </ul>
        </div>
      </div>
    </div>

    <div class="footer-bottom">
      <div class="footer-container bottom-container">
        <div class="logo-section">
          <span class="market-text">Market</span>
          <span class="phone-text">Phone</span>
        </div>
        
        <div class="footer-links">
          <a href="#">Condiciones de uso</a>
          <a href="#">Aviso de privacidad</a>
          <a href="#">Ayuda</a>
        </div>

        <p class="copyright">
          © 2024-2025, MarketPhone.com, Inc. o sus afiliados
        </p>
      </div>
    </div>
  </footer>
</template>

<script setup>
const scrollToTop = () => {
  window.scrollTo({
    top: 0,
    behavior: 'smooth'
  });
};
</script>

<style scoped>
.site-footer {
  background-color: #232F3E; /* Slightly lighter than header for contrast or standard Amazon footer dark */
  color: #DDD;
  font-family: 'Outfit', sans-serif;
  margin-top: auto;
}

/* Back to Top */
.footer-top {
  background-color: #37475A;
  text-align: center;
}

.back-to-top {
  background: none;
  border: none;
  color: white;
  padding: 1rem;
  width: 100%;
  cursor: pointer;
  font-size: 0.85rem;
  font-weight: 600;
  transition: background-color 0.2s;
}

.back-to-top:hover {
  background-color: #485769;
}

/* Middle Section */
.footer-middle {
  background-color: #232F3E;
  padding: 3rem 0;
  border-bottom: 1px solid #3a4553;
}

.footer-container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 1.5rem;
}

.footer-middle .footer-container {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
  gap: 2rem;
}

.footer-column h3 {
  color: white;
  font-size: 1rem;
  font-weight: 700;
  margin-bottom: 1rem;
}

.footer-column ul {
  list-style: none;
  padding: 0;
  margin: 0;
}

.footer-column li {
  margin-bottom: 0.5rem;
}

.footer-column a {
  color: #DDD;
  text-decoration: none;
  font-size: 0.85rem;
  transition: text-decoration 0.2s;
}

.footer-column a:hover {
  text-decoration: underline;
}

/* Bottom Section */
.footer-bottom {
  background-color: #131A22;
  padding: 2rem 0;
  text-align: center;
}

.bottom-container {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 1rem;
}

.logo-section {
  font-size: 1.5rem;
  font-weight: 700;
  margin-bottom: 0.5rem;
}

.market-text { color: white; }
.phone-text { color: #93C5FD; }

.footer-links {
  display: flex;
  gap: 1.5rem;
  flex-wrap: wrap;
  justify-content: center;
}

.footer-links a {
  color: #DDD;
  text-decoration: none;
  font-size: 0.8rem;
}

.footer-links a:hover {
  text-decoration: underline;
}

.copyright {
  color: #999;
  font-size: 0.75rem;
  margin-top: 0.5rem;
}

@media (max-width: 768px) {
  .footer-middle .footer-container {
    grid-template-columns: 1fr 1fr;
  }
}

@media (max-width: 480px) {
  .footer-middle .footer-container {
    grid-template-columns: 1fr;
    text-align: center;
  }
}
</style>
