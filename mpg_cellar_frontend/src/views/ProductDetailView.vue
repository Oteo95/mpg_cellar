<template>
  <section class="product-detail">
    <div v-if="wine" class="detail-container">
      <img :src="wine.image" :alt="wine.name" class="wine-image" />
      <div class="info">
        <h1>{{ wine.name }}</h1>
        <p class="price">\${{ wine.price.toFixed(2) }}</p>
        <p class="description">This is a fine wine from a prestigious vineyard.</p>
        <button @click="addToCart" class="add-to-cart">Add to Cart</button>
      </div>
    </div>
    <div v-else>
      <p>Wine not found.</p>
    </div>
  </section>
</template>

<script setup>
import { ref } from 'vue';
import { useRoute, useRouter } from 'vue-router';

const route = useRoute();
const router = useRouter();

const wines = [
  { id: 1, name: 'Chateau Margaux 2015', price: 450, image: '/images/margaux2015.jpg' },
  { id: 2, name: 'Penfolds Grange 2016', price: 600, image: '/images/penfolds2016.jpg' },
  { id: 3, name: 'Domaine de la Romanée-Conti 2014', price: 1200, image: '/images/romanee2014.jpg' },
  { id: 4, name: 'Screaming Eagle Cabernet 2017', price: 3000, image: '/images/screamingeagle2017.jpg' },
  { id: 5, name: 'Opus One 2018', price: 400, image: '/images/opusone2018.jpg' },
];

const wine = ref(null);

const findWine = () => {
  const id = parseInt(route.params.id);
  wine.value = wines.find(w => w.id === id) || null;
};

const addToCart = () => {
  alert(`Added ${wine.value.name} to cart.`);
};

findWine();
</script>

<style scoped>
.product-detail {
  padding: 2rem;
  font-family: 'Helvetica Neue', Arial, sans-serif;
  color: #333;
}

.detail-container {
  display: flex;
  gap: 2rem;
  flex-wrap: wrap;
  justify-content: center;
  align-items: center;
}

.wine-image {
  max-width: 300px;
  border-radius: 8px;
  box-shadow: 0 2px 8px rgba(0,0,0,0.1);
}

.info {
  max-width: 400px;
}

.price {
  font-size: 1.5rem;
  color: #7b1f24;
  font-weight: 700;
  margin: 0.5rem 0;
}

.description {
  margin: 1rem 0;
  font-size: 1rem;
  color: #555;
}

.add-to-cart {
  background-color: #7b1f24;
  color: white;
  border: none;
  padding: 0.75rem 1.5rem;
  font-size: 1rem;
  border-radius: 6px;
  cursor: pointer;
  transition: background-color 0.3s ease;
}

.add-to-cart:hover {
  background-color: #a32a2f;
}
</style>
