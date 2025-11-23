<template>
  <div class="checkout-page">
    <!-- Simplified Header -->
    <header class="checkout-header">
      <div class="header-container">
        <NuxtLink to="/home" class="logo-link">
          <span class="market-text">Market</span>
          <span class="phone-text">Phone</span>
        </NuxtLink>
        <h1 class="checkout-title">Finalizar compra</h1>
        <div class="secure-icon">
          <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="lock-icon">
            <path stroke-linecap="round" stroke-linejoin="round" d="M16.5 10.5V6.75a4.5 4.5 0 10-9 0v3.75m-.75 11.25h10.5a2.25 2.25 0 002.25-2.25v-6.75a2.25 2.25 0 00-2.25-2.25H6.75a2.25 2.25 0 00-2.25 2.25v6.75a2.25 2.25 0 002.25 2.25z" />
          </svg>
        </div>
      </div>
    </header>

    <main class="checkout-content">
      <div class="checkout-layout">
        <!-- Main Steps Column -->
        <div class="steps-container">
          
          <!-- Step 1: Address -->
          <div class="checkout-step">
            <div class="step-header">
              <span class="step-number">1</span>
              <h2>Dirección de envío</h2>
            </div>
            <div class="step-body">
              <form class="address-form">
                <div class="form-row">
                  <div class="form-group">
                    <label>País/Región</label>
                    <select class="form-input">
                      <option>México</option>
                      <option>Estados Unidos</option>
                      <option>Colombia</option>
                    </select>
                  </div>
                </div>
                <div class="form-row">
                  <div class="form-group full-width">
                    <label>Nombre completo</label>
                    <input type="text" class="form-input" />
                  </div>
                </div>
                <div class="form-row">
                  <div class="form-group full-width">
                    <label>Dirección</label>
                    <input type="text" placeholder="Calle, número, colonia" class="form-input" />
                    <input type="text" placeholder="Apartamento, suite, unidad, etc. (opcional)" class="form-input mt-2" />
                  </div>
                </div>
                <div class="form-row two-col">
                  <div class="form-group">
                    <label>Ciudad</label>
                    <input type="text" class="form-input" />
                  </div>
                  <div class="form-group">
                    <label>Estado / Provincia</label>
                    <input type="text" class="form-input" />
                  </div>
                </div>
                <div class="form-row two-col">
                  <div class="form-group">
                    <label>Código Postal</label>
                    <input type="text" class="form-input" />
                  </div>
                  <div class="form-group">
                    <label>Número de teléfono</label>
                    <input type="text" class="form-input" />
                  </div>
                </div>
                <button type="button" class="btn-continue">Usar esta dirección</button>
              </form>
            </div>
          </div>

          <!-- Step 2: Payment -->
          <div class="checkout-step">
            <div class="step-header">
              <span class="step-number">2</span>
              <h2>Método de pago</h2>
            </div>
            <div class="step-body">
              <div class="payment-option selected">
                <input type="radio" name="payment" id="card" checked />
                <label for="card" class="payment-label">
                  <span class="payment-title">Tarjeta de crédito o débito</span>
                  <div class="card-icons">
                    <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/2/2a/Mastercard-logo.svg/1280px-Mastercard-logo.svg.png" alt="Mastercard" height="20" />
                    <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/5/5e/Visa_Inc._logo.svg/2560px-Visa_Inc._logo.svg.png" alt="Visa" height="15" />
                  </div>
                </label>
              </div>
              
              <div class="card-form">
                <div class="form-row">
                  <div class="form-group full-width">
                    <label>Número de tarjeta</label>
                    <input type="text" placeholder="0000 0000 0000 0000" class="form-input" />
                  </div>
                </div>
                <div class="form-row three-col">
                  <div class="form-group full-width">
                    <label>Nombre en la tarjeta</label>
                    <input type="text" class="form-input" />
                  </div>
                  <div class="form-group">
                    <label>Fecha exp.</label>
                    <input type="text" placeholder="MM/AA" class="form-input" />
                  </div>
                  <div class="form-group">
                    <label>CVV</label>
                    <input type="text" placeholder="123" class="form-input" />
                  </div>
                </div>
              </div>

              <div class="payment-option">
                <input type="radio" name="payment" id="paypal" />
                <label for="paypal" class="payment-label">
                  <span class="payment-title">PayPal</span>
                  <img src="https://upload.wikimedia.org/wikipedia/commons/b/b5/PayPal.svg" alt="PayPal" height="20" />
                </label>
              </div>
            </div>
          </div>

          <!-- Step 3: Review -->
          <div class="checkout-step">
            <div class="step-header">
              <span class="step-number">3</span>
              <h2>Revisar artículos y envío</h2>
            </div>
            <div class="step-body review-items">
              <div class="review-item">
                <img src="/images/phone_illustration.png" alt="Phone" class="review-img" />
                <div class="review-details">
                  <h4>iPhone 13 Pro Max - 128GB</h4>
                  <p class="price">$899.99</p>
                  <p class="qty">Cantidad: 1</p>
                </div>
              </div>
              <div class="review-item">
                <img src="/images/phone_illustration.png" alt="Phone" class="review-img" />
                <div class="review-details">
                  <h4>Samsung Galaxy S22 Ultra 5G</h4>
                  <p class="price">$750.50</p>
                  <p class="qty">Cantidad: 2</p>
                </div>
              </div>
            </div>
          </div>

        </div>

        <!-- Order Summary Sidebar -->
        <aside class="summary-sidebar">
          <div class="summary-card">
            <button class="place-order-btn">Finalizar pedido</button>
            <p class="terms-text">Al realizar tu pedido, aceptas las Condiciones de uso y la Política de privacidad de MarketPhone.</p>
            
            <div class="summary-details">
              <h3>Resumen del pedido</h3>
              <div class="summary-row">
                <span>Productos:</span>
                <span>$2,400.99</span>
              </div>
              <div class="summary-row">
                <span>Envío:</span>
                <span>$0.00</span>
              </div>
              <div class="summary-row">
                <span>Impuestos:</span>
                <span>$384.16</span>
              </div>
              <div class="summary-row total">
                <span>Total:</span>
                <span class="total-price">$2,785.15</span>
              </div>
            </div>
          </div>
        </aside>
      </div>
    </main>
  </div>
</template>

<style scoped>
.checkout-page {
  background-color: #ffffff;
  min-height: 100vh;
  font-family: 'Outfit', sans-serif;
}

.checkout-header {
  background: linear-gradient(to bottom, #f7f7f7, #eaeaea);
  border-bottom: 1px solid #d5d9d9;
  padding: 1rem 0;
}

.header-container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 1.5rem;
  display: flex;
  align-items: center;
  justify-content: space-between;
}

.logo-link {
  text-decoration: none;
  font-size: 1.5rem;
  font-weight: 700;
  display: flex;
  align-items: center;
  color: #111;
}

.market-text { color: #111; }
.phone-text { color: #2563EB; }

.checkout-title {
  font-size: 1.5rem;
  font-weight: 400;
  color: #333;
  margin: 0;
}

.secure-icon {
  color: #555;
}

.lock-icon {
  width: 24px;
  height: 24px;
}

.checkout-content {
  max-width: 1200px;
  margin: 0 auto;
  padding: 2rem 1.5rem;
}

.checkout-layout {
  display: flex;
  gap: 2rem;
}

.steps-container {
  flex: 1;
}

.checkout-step {
  margin-bottom: 2rem;
  border-bottom: 1px solid #ddd;
  padding-bottom: 1.5rem;
}

.step-header {
  display: flex;
  align-items: center;
  gap: 1rem;
  margin-bottom: 1.5rem;
}

.step-number {
  font-weight: 700;
  font-size: 1.1rem;
  color: #fff;
  background-color: #2563EB; /* Brand color */
  width: 30px;
  height: 30px;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
}

.step-header h2 {
  font-size: 1.25rem;
  color: #c45500; /* Amazon orange for headers, or use brand color */
  color: #111;
  margin: 0;
}

.step-body {
  padding-left: 3rem; /* Align with header text */
}

/* Forms */
.address-form {
  max-width: 600px;
}

.form-row {
  display: flex;
  gap: 1rem;
  margin-bottom: 1rem;
}

.two-col .form-group { flex: 1; }
.three-col .form-group { flex: 1; }

.form-group {
  display: flex;
  flex-direction: column;
}

.full-width { width: 100%; }

.form-group label {
  font-weight: 600;
  font-size: 0.9rem;
  margin-bottom: 0.25rem;
  color: #333;
}

.form-input {
  padding: 0.5rem 0.75rem;
  border: 1px solid #a6a6a6;
  border-radius: 3px;
  font-size: 0.95rem;
  outline: none;
}

.form-input:focus {
  box-shadow: 0 0 0 3px rgba(37, 99, 235, 0.2);
  border-color: #2563EB;
}

.mt-2 { margin-top: 0.5rem; }

.btn-continue {
  background-color: #FBBF24;
  border: 1px solid #F59E0B;
  padding: 0.5rem 1rem;
  border-radius: 8px;
  cursor: pointer;
  font-weight: 500;
  margin-top: 1rem;
}

/* Payment */
.payment-option {
  border: 1px solid #ddd;
  border-radius: 4px;
  padding: 1rem;
  margin-bottom: 0.5rem;
  display: flex;
  align-items: center;
  gap: 0.75rem;
  cursor: pointer;
}

.payment-option.selected {
  background-color: #fcf5ee;
  border-color: #e77600;
  border-color: #2563EB;
  background-color: #eff6ff;
}

.payment-label {
  display: flex;
  align-items: center;
  justify-content: space-between;
  width: 100%;
  cursor: pointer;
}

.payment-title {
  font-weight: 600;
  font-size: 0.95rem;
}

.card-icons {
  display: flex;
  gap: 0.5rem;
  align-items: center;
}

.card-form {
  margin: 1rem 0 1.5rem 2rem;
  max-width: 500px;
}

/* Review */
.review-item {
  display: flex;
  gap: 1rem;
  border: 1px solid #eee;
  padding: 1rem;
  border-radius: 8px;
  margin-bottom: 1rem;
}

.review-img {
  width: 80px;
  height: 80px;
  object-fit: contain;
}

.review-details h4 {
  margin: 0 0 0.25rem;
  font-size: 1rem;
}

.review-details .price {
  color: #b12704;
  font-weight: 700;
  margin: 0 0 0.25rem;
}

.review-details .qty {
  font-size: 0.85rem;
  color: #555;
  margin: 0;
}

/* Sidebar */
.summary-sidebar {
  width: 300px;
  flex-shrink: 0;
}

.summary-card {
  border: 1px solid #d5d9d9;
  border-radius: 8px;
  padding: 1.5rem;
  background: #f3f3f3;
  position: sticky;
  top: 1rem;
}

.place-order-btn {
  width: 100%;
  background-color: #FBBF24;
  border: 1px solid #F59E0B;
  padding: 0.75rem;
  border-radius: 8px;
  font-size: 1rem;
  cursor: pointer;
  box-shadow: 0 2px 5px rgba(0,0,0,0.1);
  margin-bottom: 1rem;
}

.place-order-btn:hover {
  background-color: #F59E0B;
}

.terms-text {
  font-size: 0.75rem;
  color: #565959;
  text-align: center;
  margin-bottom: 1.5rem;
  line-height: 1.4;
}

.summary-details h3 {
  font-size: 1.1rem;
  margin-bottom: 1rem;
  border-bottom: 1px solid #d5d9d9;
  padding-bottom: 0.5rem;
}

.summary-row {
  display: flex;
  justify-content: space-between;
  margin-bottom: 0.5rem;
  font-size: 0.9rem;
  color: #333;
}

.summary-row.total {
  border-top: 1px solid #d5d9d9;
  padding-top: 1rem;
  margin-top: 1rem;
  font-weight: 700;
  font-size: 1.2rem;
  color: #b12704;
}

@media (max-width: 900px) {
  .checkout-layout {
    flex-direction: column;
  }
  
  .summary-sidebar {
    width: 100%;
    order: -1;
  }
}
</style>
