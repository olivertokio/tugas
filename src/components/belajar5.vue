<script setup>
import { ref } from 'vue'

const awesome = ref(true)

function toggle() {
  awesome.value = !awesome.value
}
</script>

<template>
  <button class="btn-t" @click="toggle">Toggle</button>
  
  <div class="text">
  <h1 v-if="awesome">Vue is awesome!</h1>
  <h1 v-else>Oh no 😢</h1>
</div>
</template>

<style>
.btn-t{
  width: 300px;
  margin-top: 100px;
  margin-left: 35px;
  padding: 20px;
 
  border-radius: 10px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
  position: relative;
  top: -50px;
}

.text{
  width: 300px;
  margin-top: 100px;
  margin-left: 35px;
  padding: 20px;
 
  border-radius: 10px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
  position: relative;
  top: -400px;
}
</style>