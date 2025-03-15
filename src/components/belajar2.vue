<script setup>
import { ref } from 'vue'

const titleClass = ref('title')
</script>

<template>
  <h1 :class="titleClass">Make me red</h1>
  <h1 :class="titleClass">Make me red</h1>
  <h1 :class="titleClass">Make me red</h1>
  <h1 class="judul">Make me red</h1>
  <h1 class="judul">Make me red</h1>
</template>

<style>
.title {
  color: red;
  
}
</style>

<style>
.title {
  color: blue;
  
}
/* Style dasar */
body {
  font-family: 'Arial', sans-serif;
  background-color: #f4f4f9;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  height: 100vh;
  margin: 0;
}

/* Form input */
form {
  display: flex;
  gap: 10px;
  margin-bottom: 15px;
}




</style>

