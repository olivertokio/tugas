<script setup>
import { ref, computed } from 'vue'

const message = ref('')
const counter = ref(0)

// Fungsi untuk menambah dan mengurangi count
const increment = () => counter.value++
const decrement = () => counter.value--

// Warna berubah sesuai nilai counter
const counterColor = computed(() => {
  if (counter.value > 0) return 'green'
  if (counter.value < 0) return 'red'
  return 'black'
})
</script>

<template>
  <div class="container">
    <h1>Declarative Rendering</h1>

    <h2 :style="{ color: counterColor }">
      {{ message || "Type something..." }}
    </h2>

    <div class="input"><!-- Input untuk mengubah pesan -->
    <input  v-model="message" placeholder="Type here..." />
   </div>
    <p class="count">Count is: <span :style="{ color: counterColor }">{{ counter }}</span></p>

    <!-- Tombol untuk menambah dan mengurangi count -->
    <div class="btn-group">
      <button class="btn-min" @click="decrement">➖</button>
      <button @click="increment">➕</button>
    </div>
  </div>
</template>

<style>
/* Gaya Dasar */
body {
  font-family: Arial, sans-serif;
  text-align: center;
  background-color: #f4f4f9;
  margin: 0;
  padding: 20px;
}

.container {
  width: 300px;
  margin: auto;
  padding: 20px;
  background: white;
  border-radius: 10px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
}

h1 {
  color: #1aff00;
}

h2 {
  font-size: 20px;
  min-height: 30px;
}

input {
  width: 100%;
  padding: 10px;
  font-size: 16px;
  margin: 10px 0px;
  border: 2px solid #ccc;
  border-radius: 5px;
  outline: none;
}

input:focus {
  border-color: #42b983;
}

.count {
  font-size: 18px;
  margin: 10px 0;
}

.btn-group {
  display: flex;
  justify-content: center;
  gap: 10px;
}

button {
  background-color: #42b983;
  color: white;
  border: none;
  padding: 10px 15px;
  font-size: 16px;
  border-radius: 5px;
  cursor: pointer;
  transition: background 0.3s ease-in-out;
}

button:hover {
  background-color: #369b72;
}
</style>



