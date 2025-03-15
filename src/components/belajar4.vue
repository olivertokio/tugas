<script setup>
import { ref } from 'vue'

const text = ref('')

function onInput(e) {
  text.value = e.target.value
}
</script>

<template>
  <input  class="inputs" :value="text" @input="onInput" placeholder="Type here">
  <p>{{ text }}</p>
</template>

<style>
.inputs{
  width: 300px;
  margin-top: 100px;
  margin-left: 35px;
  padding: 20px;
  background: white;
  border-radius: 10px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
  position: relative;
  top: -1px;
}
</style>
