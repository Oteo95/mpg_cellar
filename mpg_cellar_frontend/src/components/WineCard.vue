<template>
  <div class="wine-card">
    <img :src="wine.image" :alt="wine.name" class="wine-image" />
    <h3 class="wine-name">{{ wine.name }}</h3>
    <p class="wine-price">\${{ wine.price.toFixed(2) }}</p>
    <router-link :to="`/products/${wine.id}`" class="details-link">View Details</router-link>
  </div>
</template>

<script setup>
defineProps({
  wine: {
    type: Object,
    required: true,
  },
});
</script>

<style scoped>
.wine-card {
  border: none;
  border-radius: 12px;
  padding: 1.5rem;
  width: 220px;
  text-align: center;
  font-family: 'Georgia', serif;
  background: #fff;
  box-shadow: 0 8px 20px rgba(107, 58, 58, 0.15);
  transition: box-shadow 0.3s ease, transform 0.3s ease;
  cursor: pointer;
  display: flex;
  flex-direction: column;
  align-items: center;
}

.wine-card:hover {
  box-shadow: 0 12px 30px rgba(107, 58, 58, 0.3);
  transform: translateY(-5px);
}

.wine-image {
  width: 140px;
  height: auto;
  border-radius: 8px;
  box-shadow: 0 4px 10px rgba(107, 58, 58, 0.2);
  margin-bottom: 1rem;
}

.wine-name {
  margin: 0.5rem 0 0.25rem;
  font-weight: 700;
  color: #6b3a3a;
  font-size: 1.1rem;
  letter-spacing: 0.05em;
}

.wine-price {
  margin: 0 0 0.75rem;
  color: #7a4a4a;
  font-weight: 600;
  font-size: 1rem;
}

.details-link {
  text-decoration: none;
  color: #6b3a3a;
  font-weight: 700;
  font-size: 0.9rem;
  border-bottom: 2px solid transparent;
  transition: border-color 0.3s ease, color 0.3s ease;
}

.details-link:hover {
  color: #a32a2f;
  border-color: #a32a2f;
}
</style>
