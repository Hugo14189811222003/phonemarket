<template>
  <div class="cart-page">
    <TheHeader />

    <main class="cart-container">
      <div class="cart-layout">
        <!-- Cart Items Section -->
        <div class="cart-items-section">
          <div class="cart-header">
            <h1>Carrito de compras</h1>
            <span class="price-label">Precio</span>
          </div>

          <div class="cart-list">
            <div v-for="item in cartItems" :key="item.id" class="cart-item">
              <div class="item-image">
                <img :src="item.image" :alt="item.title" />
              </div>
              
              <div class="item-details">
                <div class="item-info">
                  <h3 class="item-title">{{ item.title }}</h3>
                  <p class="item-stock">En stock</p>
                  <p class="item-shipping">Envío GRATIS</p>
                  <div class="item-actions">
                    <select v-model="item.quantity" class="qty-select">
                      <option v-for="n in 10" :key="n" :value="n">Cant: {{ n }}</option>
                    </select>
                    <span class="separator">|</span>
                    <button class="action-btn delete-btn" @click="removeItem(item.id)">Eliminar</button>
                    <span class="separator">|</span>
                    <button class="action-btn">Guardar para más tarde</button>
                  </div>
                </div>
                <div class="item-price">
                  <span class="price">${{ item.price.toFixed(2) }}</span>
                </div>
              </div>
            </div>
          </div>

          <div class="cart-subtotal-bar">
            <span class="subtotal-text">Subtotal ({{ totalItems }} productos): <strong>${{ subtotal.toFixed(2) }}</strong></span>
          </div>
        </div>

        <!-- Checkout Sidebar -->
        <aside class="checkout-sidebar">
          <div class="checkout-card">
            <div class="subtotal-summary">
              <span class="subtotal-text">Subtotal ({{ totalItems }} productos): <strong>${{ subtotal.toFixed(2) }}</strong></span>
            </div>
            <div class="gift-option">
              <label><input type="checkbox" /> Es un regalo</label>
            </div>
            <button class="checkout-btn" @click="navigateTo('/checkout')">Proceder al pago</button>
          </div>
        </aside>
      </div>
    </main>
  </div>
</template>

<script setup>
const cartItems = ref([
  {
    id: 1,
    title: 'iPhone 13 Pro Max - 128GB - Azul Sierra (Reacondicionado)',
    price: 899.99,
    image: '/images/phone_illustration.png',
    quantity: 1
  },
  {
    id: 2,
    title: 'Samsung Galaxy S22 Ultra 5G - 256GB - Negro Fantasma',
    price: 750.50,
    image: '/images/phone_illustration.png',
    quantity: 2
  }
])

const totalItems = computed(() => {
  return cartItems.value.reduce((acc, item) => acc + item.quantity, 0)
})

const subtotal = computed(() => {
  return cartItems.value.reduce((acc, item) => acc + (item.price * item.quantity), 0)
})

const removeItem = (id) => {
  cartItems.value = cartItems.value.filter(item => item.id !== id)
}
</script>

<style scoped>
.cart-page {
  background-color: #E3E6E6;
  min-height: 100vh;
}

.cart-container {
  max-width: 1500px;
  margin: 0 auto;
  padding: 2rem 1.5rem;
}

.cart-layout {
  display: flex;
  gap: 1.5rem;
}

/* Left Column: Items */
.cart-items-section {
  flex: 1;
  background: white;
  padding: 1.5rem;
  border-radius: 8px; /* Slightly rounded like modern Amazon */
}

.cart-header {
  display: flex;
  justify-content: space-between;
  align-items: flex-end;
  border-bottom: 1px solid #E5E7EB;
  padding-bottom: 1rem;
  margin-bottom: 1rem;
}

.cart-header h1 {
  font-size: 1.75rem;
  font-weight: 500;
  margin: 0;
  color: #1F2937;
}

.price-label {
  font-size: 0.9rem;
  color: #565959;
  display: none; /* Hide on mobile, show on desktop if needed */
}

@media (min-width: 768px) {
  .price-label {
    display: block;
    text-align: right;
    width: 100px;
  }
}

.cart-item {
  display: flex;
  padding: 1.5rem 0;
  border-bottom: 1px solid #E5E7EB;
}

.item-image {
  width: 180px;
  height: 180px;
  flex-shrink: 0;
  display: flex;
  align-items: center;
  justify-content: center;
  margin-right: 1.5rem;
}

.item-image img {
  max-width: 100%;
  max-height: 100%;
  object-fit: contain;
}

.item-details {
  flex: 1;
  display: flex;
  justify-content: space-between;
}

.item-title {
  font-size: 1.1rem;
  font-weight: 500;
  margin: 0 0 0.5rem;
  color: #1F2937;
  line-height: 1.3;
}

.item-stock {
  color: #007600;
  font-size: 0.85rem;
  margin-bottom: 0.25rem;
}

.item-shipping {
  font-size: 0.85rem;
  color: #565959;
  margin-bottom: 1rem;
}

.item-actions {
  display: flex;
  align-items: center;
  flex-wrap: wrap;
  gap: 0.5rem;
  font-size: 0.85rem;
}

.qty-select {
  padding: 0.25rem 0.5rem;
  border: 1px solid #D1D5DB;
  border-radius: 4px;
  background: #F0F2F2;
  box-shadow: 0 1px 2px rgba(15,17,17,0.15);
  cursor: pointer;
}

.separator {
  color: #D1D5DB;
  margin: 0 0.25rem;
}

.action-btn {
  background: none;
  border: none;
  color: #007185;
  cursor: pointer;
  padding: 0;
}

.action-btn:hover {
  text-decoration: underline;
}

.item-price {
  font-weight: 700;
  font-size: 1.2rem;
  text-align: right;
  min-width: 100px;
}

.cart-subtotal-bar {
  text-align: right;
  padding-top: 1rem;
  font-size: 1.1rem;
}

/* Right Column: Checkout */
.checkout-sidebar {
  width: 300px;
  flex-shrink: 0;
}

.checkout-card {
  background: white;
  padding: 1.5rem;
  border-radius: 8px;
}

.subtotal-summary {
  font-size: 1.1rem;
  margin-bottom: 1rem;
}

.gift-option {
  margin-bottom: 1.5rem;
  font-size: 0.9rem;
}

.checkout-btn {
  width: 100%;
  background-color: #FBBF24; /* Amazon yellow */
  border: none;
  padding: 0.75rem;
  border-radius: 8px;
  font-size: 1rem;
  cursor: pointer;
  box-shadow: 0 2px 5px rgba(213, 217, 217, 0.5);
  transition: background-color 0.2s;
}

.checkout-btn:hover {
  background-color: #F59E0B;
}

@media (max-width: 900px) {
  .cart-layout {
    flex-direction: column;
  }
  
  .checkout-sidebar {
    width: 100%;
    order: -1; /* Show checkout button on top for mobile */
  }
  
  .item-details {
    flex-direction: column;
  }
  
  .item-price {
    text-align: left;
    margin-top: 0.5rem;
  }
  
  .item-image {
    width: 100px;
    height: 100px;
  }
}
</style>
