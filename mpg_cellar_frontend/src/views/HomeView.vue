<template>
  <section class="home">
    <section class="welcome-section" :style="{ backgroundImage: 'url(/images/descarga.jpg)' }">
      <div class="welcome-content">
        <h1>Welcome to MPG Cellar</h1>
        <p>Discover our selection of fine wines.</p>
        <p class="punchline">Experience elegance in every sip.</p>
      </div>
    </section>
    <section v-for="wine in featuredWines" :key="wine.id" class="wine-section" :style="{ backgroundImage: 'url(' + wine.background + ')' }">
      <div class="wine-info">
        <h2>{{ wine.name }}</h2>
        <p class="price">\${{ wine.price.toFixed(2) }}</p>
        <router-link :to="`/products/${wine.id}`" class="details-link">View Details</router-link>
      </div>
    </section>
  </section>
</template>

<script setup>
import { ref, onMounted } from 'vue';

const featuredWines = ref([
  { id: 1, name: 'Chateau Margaux 2015', price: 450, background: '/images/bg_margaux.jpg' },
  { id: 2, name: 'Penfolds Grange 2016', price: 600, background: '/images/bg_penfolds.jpg' },
  { id: 3, name: 'Domaine de la Romanée-Conti 2014', price: 1200, background: '/images/bg_romanee.jpg' },
]);

const animateSections = () => {
  const sections = document.querySelectorAll('.wine-section, .welcome-section');
  sections.forEach((section, index) => {
    section.style.animationDelay = `${index * 0.4}s`;
    section.classList.add('fade-in-up');
  });
};

onMounted(() => {
  animateSections();
});
</script>

<style scoped>

.home {
  font-family: 'Georgia', serif;
  color: #4b2e2e;
  background: linear-gradient(135deg, #f9f5f2 0%, #e6dfdb 100%);
  min-height: 100vh;
  display: flex;
  flex-direction: column;
}

.welcome-section {
  position: relative;
  height: 400px;
  background-size: cover;
  background-position: center;
  margin: 0;
  width: 100vw;
  box-shadow: inset 0 0 0 1000px rgba(107, 58, 58, 0.4);
  display: flex;
  justify-content: center;
  align-items: center;
  color: white;
  cursor: default;
  opacity: 0;
  transform: translateY(20px);
  transition: none;
  border-radius: 0;
}

.welcome-section:hover {
  transform: none;
  box-shadow: inset 0 0 0 1000px rgba(107, 58, 58, 0.4);
}


.welcome-content {
  background: transparent;
  padding: 0;
  border-radius: 0;
  max-width: none;
  text-align: center;
}

.welcome-content h1 {
  font-size: 3.5rem;
  font-weight: 700;
  margin-bottom: 1rem;
  letter-spacing: 0.1em;
  text-transform: uppercase;
}

.welcome-content p {
  font-size: 1.5rem;
  font-style: italic;
  margin-bottom: 0.5rem;
}

.punchline {
  font-weight: 700;
  font-size: 1.75rem;
  color: #a32a2f;
  margin-top: 1rem;
}

.wine-section {
  position: relative;
  height: 400px;
  background-size: cover;
  background-position: center;
  display: flex;
  align-items: center;
  padding: 2rem 10vw;
  color: white;
  cursor: default;
  opacity: 0;
  transform: translateY(20px);
  margin: 0;
  width: 100vw;
  box-shadow: inset 0 0 0 1000px rgba(107, 58, 58, 0.4);
  transition: none;
}

.wine-section:hover {
  transform: none;
  box-shadow: inset 0 0 0 1000px rgba(107, 58, 58, 0.4);
}

.wine-info {
  background: transparent;
  padding: 0;
  border-radius: 0;
  width: auto;
  max-width: none;
  text-align: left;
}

.wine-info h2 {
  margin: 0 0 0.5rem;
  font-size: 2.5rem;
  font-weight: 700;
  letter-spacing: 0.05em;
}

.price {
  font-size: 1.75rem;
  font-weight: 600;
  margin-bottom: 0.5rem;
}

.details-link {
  color: #f9f5f2;
  font-weight: 600;
  text-decoration: underline;
  font-size: 1.5rem;
}

.details-link:hover {
  color: #e6dfdb;
}

@keyframes fadeInUp {
  from {
    opacity: 0;
    transform: translateY(20px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

.fade-in-up {
  animation: fadeInUp 0.6s forwards;
}
</style>
