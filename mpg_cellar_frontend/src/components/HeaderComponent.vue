<template>
  <header class="header">
    <div class="logo">MPG Cellar</div>
    <nav>
      <ul>
        <li><router-link to="/">Home</router-link></li>
        <li><router-link to="/products">Wines</router-link></li>
      </ul>
    </nav>
  </header>
</template>

<script setup>
</script>

<style scoped>
.header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 1.5rem 3rem;
  background-color: #fff;
  border-bottom: 2px solid #7b1f24;
  font-family: 'Georgia', serif;
  box-shadow: 0 2px 8px rgba(107, 58, 58, 0.1);
}

.logo {
  font-weight: 900;
  font-size: 1.75rem;
  color: #7b1f24; /* deep wine red */
  letter-spacing: 0.1em;
  text-transform: uppercase;
}

nav ul {
  list-style: none;
  display: flex;
  gap: 2rem;
  margin: 0;
  padding: 0;
}

nav a {
  text-decoration: none;
  color: #6b3a3a;
  font-weight: 700;
  font-size: 1rem;
  transition: color 0.3s ease, border-bottom 0.3s ease;
  border-bottom: 2px solid transparent;
  padding-bottom: 0.2rem;
}

nav a:hover {
  color: #a32a2f;
  border-bottom: 2px solid #a32a2f;
}
</style>
