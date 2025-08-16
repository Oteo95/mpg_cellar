<template>
  <section class="products">
    <h1>Our Wines</h1>
    <div class="product-list">
      <WineCard v-for="wine in wines" :key="wine.id" :wine="wine" />
    </div>
  </section>
</template>

<script setup>
import WineCard from '../components/WineCard.vue';

const wines = [
  { id: 1, name: 'Chateau Margaux 2015', price: 450, image: '/images/margaux2015.jpg' },
  { id: 2, name: 'Penfolds Grange 2016', price: 600, image: '/images/penfolds2016.jpg' },
  { id: 3, name: 'Domaine de la Romanée-Conti 2014', price: 1200, image: '/images/romanee2014.jpg' },
  { id: 4, name: 'Screaming Eagle Cabernet 2017', price: 3000, image: '/images/screamingeagle2017.jpg' },
  { id: 5, name: 'Opus One 2018', price: 400, image: '/images/opusone2018.jpg' },
];
</script>

<style scoped>
.products {
  padding: 2rem;
  font-family: 'Helvetica Neue', Arial, sans-serif;
  color: #333;
  text-align: center;
}

.product-list {
  display: flex;
  justify-content: center;
  gap: 2rem;
  margin-top: 2rem;
  flex-wrap: wrap;
}
</style>
