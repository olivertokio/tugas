<script setup>
import { ref } from 'vue'

const btnclass = ref('btn')
const count = ref(0)

const increment = () => count.value++
</script>

<template>
  <div class="containerss">
    <p class="count">Count: <span>{{ count }}</span></p>
    <button :class="btnclass" @click="increment">Click me</button>
  </div>
</template>


<style>
.containerss{
  width: 300px;
  margin-top: 100px;
  margin-left: 35px;
  padding: 20px;
  background: white;
  border-radius: 10px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
  position: relative;
  top: 120px;
}
</style>