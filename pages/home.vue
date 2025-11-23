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
              <li><label><input type="checkbox" value="Apple" v-model="selectedBrands"> Apple</label></li>
              <li><label><input type="checkbox" value="Samsung" v-model="selectedBrands"> Samsung</label></li>
              <li><label><input type="checkbox" value="Xiaomi" v-model="selectedBrands"> Xiaomi</label></li>
              <li><label><input type="checkbox" value="Google" v-model="selectedBrands"> Google</label></li>
            </ul>
          </div>
          
          <div class="filter-section">
            <h3>Condición</h3>
            <ul>
              <li><label><input type="checkbox" value="Nuevo" v-model="selectedConditions"> Nuevo</label></li>
              <li><label><input type="checkbox" value="Como nuevo" v-model="selectedConditions"> Como nuevo</label></li>
              <li><label><input type="checkbox" value="Bueno" v-model="selectedConditions"> Bueno</label></li>
            </ul>
          </div>

          <div class="filter-section">
            <h3>Precio</h3>
            <ul>
              <li><label><input type="checkbox" value="under200" v-model="selectedPriceRanges"> Menos de $200</label></li>
              <li><label><input type="checkbox" value="200to500" v-model="selectedPriceRanges"> $200 - $500</label></li>
              <li><label><input type="checkbox" value="over500" v-model="selectedPriceRanges"> Más de $500</label></li>
            </ul>
          </div>
        </aside>

        <!-- Product Grid -->
        <div class="products-grid">
          <ProductCard 
            v-for="phone in filteredPhones" 
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
const searchQuery = useState('searchQuery', () => '')

// Filter states
const selectedBrands = ref([])
const selectedConditions = ref([])
const selectedPriceRanges = ref([])

// Dummy data with added fields for filtering
const phones = ref([
  {
    id: 1,
    title: 'iPhone 13 Pro Max - 128GB - Azul Sierra (Reacondicionado)',
    brand: 'Apple',
    condition: 'Como nuevo',
    price: 899.99,
    image: '/images/phone_illustration.png', 
    ratingCount: 1240,
    deliveryDate: 'Lunes, 25 Nov'
  },
  {
    id: 2,
    title: 'Samsung Galaxy S22 Ultra 5G - 256GB - Negro Fantasma',
    brand: 'Samsung',
    condition: 'Nuevo',
    price: 750.50,
    image: '/images/phone_illustration.png',
    ratingCount: 856,
    deliveryDate: 'Martes, 26 Nov'
  },
  {
    id: 3,
    title: 'Google Pixel 7 Pro - 128GB - Hazel',
    brand: 'Google',
    condition: 'Nuevo',
    price: 649.00,
    image: '/images/phone_illustration.png',
    ratingCount: 432,
    deliveryDate: 'Mañana, 24 Nov'
  },
  {
    id: 4,
    title: 'Xiaomi Redmi Note 12 - 128GB - Gris Ónix',
    brand: 'Xiaomi',
    condition: 'Nuevo',
    price: 199.99,
    image: '/images/phone_illustration.png',
    ratingCount: 2100,
    deliveryDate: 'Lunes, 25 Nov'
  },
  {
    id: 5,
    title: 'iPhone 12 - 64GB - Blanco (Usado - Bueno)',
    brand: 'Apple',
    condition: 'Bueno',
    price: 350.00,
    image: '/images/phone_illustration.png',
    ratingCount: 560,
    deliveryDate: 'Miércoles, 27 Nov'
  },
  {
    id: 6,
    title: 'Samsung Galaxy A54 5G - 128GB - Violeta',
    brand: 'Samsung',
    condition: 'Nuevo',
    price: 329.99,
    image: '/images/phone_illustration.png',
    ratingCount: 120,
    deliveryDate: 'Mañana, 24 Nov'
  }
])

const filteredPhones = computed(() => {
  return phones.value.filter(phone => {
    // 1. Search Query
    if (searchQuery.value && !phone.title.toLowerCase().includes(searchQuery.value.toLowerCase())) {
      return false
    }

    // 2. Brand Filter
    if (selectedBrands.value.length > 0 && !selectedBrands.value.includes(phone.brand)) {
      return false
    }

    // 3. Condition Filter
    if (selectedConditions.value.length > 0 && !selectedConditions.value.includes(phone.condition)) {
      return false
    }

    // 4. Price Filter
    if (selectedPriceRanges.value.length > 0) {
      const matchesPrice = selectedPriceRanges.value.some(range => {
        if (range === 'under200') return phone.price < 200
        if (range === '200to500') return phone.price >= 200 && phone.price <= 500
        if (range === 'over500') return phone.price > 500
        return false
      })
      if (!matchesPrice) return false
    }

    return true
  })
})
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
