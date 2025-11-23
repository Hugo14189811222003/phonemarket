<template>
  <header class="site-header">
    <div class="header-container">
      <!-- Logo -->
      <NuxtLink to="/" class="logo-link">
        <span class="market-text">Market</span>
        <span class="phone-text">Phone</span>
      </NuxtLink>

      <!-- Search Bar -->
      <div class="search-container">
        <div class="search-wrapper">
          <input type="text" placeholder="Buscar teléfonos, marcas..." class="search-input" />
          <button class="search-btn">
            <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="2" stroke="currentColor" class="search-icon">
              <path stroke-linecap="round" stroke-linejoin="round" d="M21 21l-5.197-5.197m0 0A7.5 7.5 0 105.196 5.196a7.5 7.5 0 0010.607 10.607z" />
            </svg>
          </button>
        </div>
      </div>

      <!-- Actions -->
      <div class="header-actions">
        <NuxtLink to="/login" class="action-link">
          <div class="action-text">
            <span class="small-text">Hola, identifícate</span>
            <span class="bold-text">Cuenta y Listas</span>
          </div>
        </NuxtLink>

        <NuxtLink to="/cart" class="cart-link">
          <div class="cart-icon-wrapper">
            <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="2" stroke="currentColor" class="cart-icon">
              <path stroke-linecap="round" stroke-linejoin="round" d="M2.25 3h1.386c.51 0 .955.343 1.087.835l.383 1.437M7.5 14.25a3 3 0 00-3 3h15.75m-12.75-3h11.218c1.121-2.3 2.1-4.684 2.924-7.138a60.114 60.114 0 00-16.536-1.84M7.5 14.25L5.106 5.272M6 20.25a.75.75 0 11-1.5 0 .75.75 0 011.5 0zm12.75 0a.75.75 0 11-1.5 0 .75.75 0 011.5 0z" />
            </svg>
            <span class="cart-count">0</span>
          </div>
          <span class="bold-text cart-text">Carrito</span>
        </NuxtLink>
      </div>
    </div>
  </header>
</template>

<style scoped>
.site-header {
  background-color: #131921; /* Amazon dark header or use var(--primary-dark) */
  background-color: var(--primary-dark);
  color: white;
  padding: 0.75rem 0;
  position: sticky;
  top: 0;
  z-index: 100;
}

.header-container {
  max-width: 1400px;
  margin: 0 auto;
  padding: 0 1.5rem;
  display: flex;
  align-items: center;
  gap: 2rem;
}

.logo-link {
  text-decoration: none;
  font-size: 1.5rem;
  font-weight: 700;
  display: flex;
  align-items: center;
  color: white;
}

.market-text {
  color: white;
}

.phone-text {
  color: #93C5FD; /* Lighter blue */
}

/* Search */
.search-container {
  flex: 1;
  max-width: 800px;
}

.search-wrapper {
  display: flex;
  border-radius: 4px;
  overflow: hidden;
  background: white;
}

.search-input {
  flex: 1;
  padding: 0.75rem 1rem;
  border: none;
  outline: none;
  font-size: 1rem;
}

.search-btn {
  background-color: #FBBF24; /* Amazon yellow/orange accent or secondary color */
  border: none;
  padding: 0 1rem;
  cursor: pointer;
  display: flex;
  align-items: center;
  justify-content: center;
  transition: background-color 0.2s;
}

.search-btn:hover {
  background-color: #F59E0B;
}

.search-icon {
  width: 24px;
  height: 24px;
  color: #1F2937;
}

/* Actions */
.header-actions {
  display: flex;
  align-items: center;
  gap: 1.5rem;
}

.action-link {
  text-decoration: none;
  color: white;
  display: flex;
  align-items: center;
}

.action-text {
  display: flex;
  flex-direction: column;
  line-height: 1.2;
}

.small-text {
  font-size: 0.75rem;
  color: #D1D5DB;
}

.bold-text {
  font-weight: 700;
  font-size: 0.9rem;
}

.cart-link {
  display: flex;
  align-items: flex-end;
  text-decoration: none;
  color: white;
  gap: 0.25rem;
}

.cart-icon-wrapper {
  position: relative;
}

.cart-icon {
  width: 32px;
  height: 32px;
}

.cart-count {
  position: absolute;
  top: -4px;
  right: -4px;
  background-color: #FBBF24;
  color: #1F2937;
  font-size: 0.75rem;
  font-weight: 700;
  width: 18px;
  height: 18px;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
}

.cart-text {
  margin-bottom: 2px;
}

@media (max-width: 768px) {
  .header-container {
    flex-wrap: wrap;
    gap: 1rem;
  }
  
  .search-container {
    order: 3;
    width: 100%;
    max-width: none;
  }
  
  .cart-text {
    display: none;
  }
}
</style>
