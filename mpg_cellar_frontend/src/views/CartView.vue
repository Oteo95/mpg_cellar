<template>
  <section class="cart">
    <h1>Shopping Cart</h1>
    <div v-if="cartItems.length > 0" class="cart-items">
      <div v-for="item in cartItems" :key="item.id" class="cart-item">
        <img :src="item.image" :alt="item.name" class="cart-item-image" />
        <div class="cart-item-info">
          <h3>{{ item.name }}</h3>
          <p>Price: \${{ item.price.toFixed(2) }}</p>
          <label>Quantity:
            <input type="number" v-model.number="item.quantity" min="1" @change="updateQuantity(item)" />
          </label>
          <button @click="removeItem(item.id)" class="remove-button">Remove</button>
        </div>
      </div>
      <div class="cart-total">
        <strong>Total: \${{ totalPrice.toFixed(2) }}</strong>
      </div>
      <router-link to="/checkout" class="checkout-button">Proceed to Checkout</router-link>
    </div>
    <div v-else>
      <p>Your cart is empty.</p>
    </div>
  </section>
</template>

<script setup>
import { reactive, computed } from 'vue';

const cartItems = reactive([
  // Example item structure
  // { id: 1, name: 'Chateau Margaux 2015', price: 450, image: '/images/margaux2015.jpg', quantity: 1 }
]);

const totalPrice = computed(() =>
  cartItems.reduce((total, item) => total + item.price * item.quantity, 0)
);

const updateQuantity = (item) => {
  if (item.quantity < 1) {
    item.quantity = 1;
  }
};

const removeItem = (id) => {
  const index = cartItems.findIndex(item => item.id === id);
  if (index !== -1) {
    cartItems.splice(index, 1);
  }
};
</script>

<style scoped>
.cart {
  padding: 2rem;
  font-family: 'Helvetica Neue', Arial, sans-serif;
  color: #333;
}

.cart-items {
  display: flex;
  flex-direction: column;
  gap: 1rem;
}

.cart-item {
  display: flex;
  gap: 1rem;
  border-bottom: 1px solid #eee;
  padding-bottom: 1rem;
}

.cart-item-image {
  width: 100px;
  border-radius: 8px;
}

.cart-item-info {
  flex-grow: 1;
}

.remove-button {
  background-color: #a32a2f;
  color: white;
  border: none;
  padding: 0.5rem 1rem;
  border-radius: 6px;
  cursor: pointer;
  margin-top: 0.5rem;
  transition: background-color 0.3s ease;
}

.remove-button:hover {
  background-color: #7b1f24;
}

.cart-total {
  margin-top: 1rem;
  font-size: 1.25rem;
  text-align: right;
}

.checkout-button {
  display: inline-block;
  margin-top: 1rem;
  background-color: #7b1f24;
  color: white;
  padding: 0.75rem 1.5rem;
  border-radius: 6px;
  text-decoration: none;
  font-weight: 600;
  transition: background-color 0.3s ease;
}

.checkout-button:hover {
  background-color: #a32a2f;
}
</style>
