<template>
  <div class="home-page">
    <TheHeader />
    
    <main class="main-content">
      <!-- Banner / Hero -->
      <div class="hero-banner">
        <div class="hero-content">
          <h2>Encuentra tu próximo smartphone</h2>
          <p>Las mejores marcas a precios increíbles. Garantía de calidad.</p>
        </div>
      </div>

      <div class="market-layout">
        <!-- Sidebar Filters -->
        <aside class="filters-sidebar">
          <div class="filter-section">
            <h3>Marcas</h3>
            <ul>
              <li><label><input type="checkbox"> Apple</label></li>
              <li><label><input type="checkbox"> Samsung</label></li>
              <li><label><input type="checkbox"> Xiaomi</label></li>
              <li><label><input type="checkbox"> Google</label></li>
            </ul>
          </div>
          
          <div class="filter-section">
            <h3>Condición</h3>
            <ul>
              <li><label><input type="checkbox"> Nuevo</label></li>
              <li><label><input type="checkbox"> Como nuevo</label></li>
              <li><label><input type="checkbox"> Bueno</label></li>
            </ul>
          </div>

          <div class="filter-section">
            <h3>Precio</h3>
            <ul>
              <li><label><input type="checkbox"> Menos de $200</label></li>
              <li><label><input type="checkbox"> $200 - $500</label></li>
              <li><label><input type="checkbox"> Más de $500</label></li>
            </ul>
          </div>
        </aside>

        <!-- Product Grid -->
        <div class="products-grid">
          <ProductCard 
            v-for="phone in phones" 
            :key="phone.id"
            :title="phone.title"
            :price="phone.price"
            :image="phone.image"
            :ratingCount="phone.ratingCount"
            :deliveryDate="phone.deliveryDate"
          />
        </div>
      </div>
    </main>
  </div>
</template>

<script setup>
// Dummy data
const phones = ref([
  {
    id: 1,
    title: 'iPhone 13 Pro Max - 128GB - Azul Sierra (Reacondicionado)',
    price: 899.99,
    image: '/images/phone_illustration.png', // Placeholder
    ratingCount: 1240,
    deliveryDate: 'Lunes, 25 Nov'
  },
  {
    id: 2,
    title: 'Samsung Galaxy S22 Ultra 5G - 256GB - Negro Fantasma',
    price: 750.50,
    image: '/images/phone_illustration.png',
    ratingCount: 856,
    deliveryDate: 'Martes, 26 Nov'
  },
  {
    id: 3,
    title: 'Google Pixel 7 Pro - 128GB - Hazel',
    price: 649.00,
    image: '/images/phone_illustration.png',
    ratingCount: 432,
    deliveryDate: 'Mañana, 24 Nov'
  },
  {
    id: 4,
    title: 'Xiaomi Redmi Note 12 - 128GB - Gris Ónix',
    price: 199.99,
    image: '/images/phone_illustration.png',
    ratingCount: 2100,
    deliveryDate: 'Lunes, 25 Nov'
  },
  {
    id: 5,
    title: 'iPhone 12 - 64GB - Blanco (Usado - Bueno)',
    price: 350.00,
    image: '/images/phone_illustration.png',
    ratingCount: 560,
    deliveryDate: 'Miércoles, 27 Nov'
  },
  {
    id: 6,
    title: 'Samsung Galaxy A54 5G - 128GB - Violeta',
    price: 329.99,
    image: '/images/phone_illustration.png',
    ratingCount: 120,
    deliveryDate: 'Mañana, 24 Nov'
  }
])
</script>

<style scoped>
.home-page {
  background-color: #E3E6E6; /* Amazon light gray bg */
  min-height: 100vh;
}

.main-content {
  max-width: 1500px;
  margin: 0 auto;
}

.hero-banner {
  background: linear-gradient(to right, #2563EB, #1E40AF);
  color: white;
  padding: 3rem 2rem;
  text-align: center;
  margin-bottom: -2rem; /* Pull content up slightly */
  padding-bottom: 4rem;
}

.hero-content h2 {
  font-size: 2.5rem;
  margin: 0 0 1rem;
}

.market-layout {
  display: flex;
  gap: 1.5rem;
  padding: 0 1.5rem 2rem;
  max-width: 1400px;
  margin: 0 auto;
}

.filters-sidebar {
  width: 250px;
  flex-shrink: 0;
  background: white;
  padding: 1.5rem;
  border-radius: 8px;
  height: fit-content;
  margin-top: -2rem; /* Overlap banner */
  box-shadow: 0 4px 6px rgba(0,0,0,0.05);
}

.filter-section {
  margin-bottom: 2rem;
  border-bottom: 1px solid #E5E7EB;
  padding-bottom: 1rem;
}

.filter-section:last-child {
  border-bottom: none;
}

.filter-section h3 {
  font-size: 1rem;
  margin-bottom: 0.75rem;
  color: #1F2937;
}

.filter-section ul {
  list-style: none;
  padding: 0;
  margin: 0;
}

.filter-section li {
  margin-bottom: 0.5rem;
  font-size: 0.9rem;
  color: #374151;
}

.filter-section label {
  cursor: pointer;
  display: flex;
  align-items: center;
  gap: 0.5rem;
}

.products-grid {
  flex: 1;
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
  gap: 1.5rem;
  margin-top: -2rem; /* Overlap banner */
}

@media (max-width: 768px) {
  .market-layout {
    flex-direction: column;
  }
  
  .filters-sidebar {
    width: 100%;
    margin-top: 0;
  }
  
  .products-grid {
    margin-top: 0;
  }
}
</style>
