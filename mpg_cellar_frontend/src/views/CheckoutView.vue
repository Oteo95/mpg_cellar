<template>
  <section class="checkout">
    <h1>Checkout</h1>
    <form @submit.prevent="submitOrder">
      <label>
        Name:
        <input type="text" v-model="form.name" required />
      </label>
      <label>
        Email:
        <input type="email" v-model="form.email" required />
      </label>
      <label>
        Address:
        <textarea v-model="form.address" required></textarea>
      </label>
      <label>
        Payment Method:
        <select v-model="form.paymentMethod" required>
          <option value="credit-card">Credit Card</option>
          <option value="paypal">PayPal</option>
        </select>
      </label>
      <button type="submit">Place Order</button>
    </form>
  </section>
</template>

<script setup>
import { reactive } from 'vue';

const form = reactive({
  name: '',
  email: '',
  address: '',
  paymentMethod: 'credit-card',
});

const submitOrder = () => {
  alert(`Thank you, ${form.name}! Your order has been placed.`);
  // Here you would normally handle order submission logic
};
</script>

<style scoped>
.checkout {
  padding: 2rem;
  font-family: 'Helvetica Neue', Arial, sans-serif;
  color: #333;
  max-width: 400px;
  margin: 0 auto;
}

form {
  display: flex;
  flex-direction: column;
  gap: 1rem;
}

label {
  display: flex;
  flex-direction: column;
  font-weight: 600;
}

input, textarea, select {
  margin-top: 0.5rem;
  padding: 0.5rem;
  font-size: 1rem;
  border: 1px solid #ccc;
  border-radius: 6px;
  font-family: 'Helvetica Neue', Arial, sans-serif;
}

button {
  background-color: #7b1f24;
  color: white;
  border: none;
  padding: 0.75rem;
  font-size: 1rem;
  border-radius: 6px;
  cursor: pointer;
  transition: background-color 0.3s ease;
}

button:hover {
  background-color: #a32a2f;
}
</style>
