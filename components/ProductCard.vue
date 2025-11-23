<template>
  <div class="product-card">
    <div class="image-container">
      <img :src="image" :alt="title" class="product-image" />
    </div>
    <div class="product-info">
      <h3 class="product-title">{{ title }}</h3>
      <div class="rating">
        <span class="stars">★★★★☆</span>
        <span class="count">({{ ratingCount }})</span>
      </div>
      <div class="price-block">
        <span class="currency">$</span>
        <span class="price-whole">{{ Math.floor(price) }}</span>
        <span class="price-fraction">{{ getFraction(price) }}</span>
      </div>
      <p class="delivery-info">Entrega GRATIS el <strong>{{ deliveryDate }}</strong></p>
      <button class="add-btn">Agregar al carrito</button>
    </div>
  </div>
</template>

<script setup>
const props = defineProps({
  title: String,
  price: Number,
  image: String,
  ratingCount: Number,
  deliveryDate: String
})

const getFraction = (price) => {
  const fraction = (price % 1).toFixed(2).substring(2);
  return fraction;
}
</script>

<style scoped>
.product-card {
  background: white;
  border: 1px solid #E5E7EB;
  border-radius: 8px;
  padding: 1rem;
  display: flex;
  flex-direction: column;
  height: 100%;
  transition: box-shadow 0.2s;
}

.product-card:hover {
  box-shadow: 0 10px 15px -3px rgba(0, 0, 0, 0.1);
}

.image-container {
  height: 200px;
  display: flex;
  align-items: center;
  justify-content: center;
  margin-bottom: 1rem;
  background-color: #F9FAFB;
  border-radius: 4px;
}

.product-image {
  max-height: 100%;
  max-width: 100%;
  object-fit: contain;
}

.product-info {
  display: flex;
  flex-direction: column;
  flex: 1;
}

.product-title {
  font-size: 1rem;
  font-weight: 500;
  line-height: 1.4;
  margin: 0 0 0.5rem;
  color: #1F2937;
  display: -webkit-box;
  -webkit-line-clamp: 2;
  -webkit-box-orient: vertical;
  overflow: hidden;
}

.rating {
  margin-bottom: 0.5rem;
  font-size: 0.9rem;
}

.stars {
  color: #F59E0B;
  margin-right: 0.25rem;
}

.count {
  color: #007185; /* Amazon link color */
}

.price-block {
  display: flex;
  align-items: flex-start;
  margin-bottom: 0.5rem;
}

.currency {
  font-size: 0.85rem;
  margin-top: 0.3rem;
}

.price-whole {
  font-size: 1.75rem;
  font-weight: 700;
}

.price-fraction {
  font-size: 0.85rem;
  margin-top: 0.3rem;
}

.delivery-info {
  font-size: 0.85rem;
  color: #565959;
  margin-bottom: 1rem;
}

.add-btn {
  margin-top: auto;
  background-color: #FBBF24;
  border: none;
  padding: 0.5rem;
  border-radius: 20px;
  font-size: 0.9rem;
  cursor: pointer;
  transition: background-color 0.2s;
}

.add-btn:hover {
  background-color: #F59E0B;
}
</style>
