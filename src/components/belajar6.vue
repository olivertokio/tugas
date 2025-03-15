<script setup>
import { ref, computed } from 'vue'

// ID unik untuk setiap todo
let id = 1

const newTodo = ref('')
const hideCompleted = ref(false)
const todos = ref([
  { id: id++, text: 'Learn HTML', done: false },
  { id: id++, text: 'Learn JavaScript', done: false },
  { id: id++, text: 'Learn Vue', done: false }
])

// Tambah todo baru
function addTodo() {
  if (newTodo.value.trim() === '') return // Cegah input kosong
  todos.value.push({ id: id++, text: newTodo.value.trim(), done: false })
  newTodo.value = ''
}

// Hapus todo
function removeTodo(todo) {
  todos.value = todos.value.filter((t) => t.id !== todo.id)
}

// Filter tugas berdasarkan apakah sudah selesai atau tidak
const filteredTodos = computed(() => {
  return hideCompleted.value ? todos.value.filter(todo => !todo.done) : todos.value
})
</script>

<template>
  <div class="containerr">
    <h2>Vue Todo List ✅</h2>

    <!-- Form Input -->
    <form @submit.prevent="addTodo">
      <input v-model="newTodo" placeholder="Add new todo..." />
      <button type="submit">Add</button>
    </form>

    <!-- Conditional Rendering: Jika daftar kosong -->
    <p v-if="todos.length === 0">🎉 No todos left! 🎉</p>

    <!-- Daftar Todo -->
    <transition-group name="fade" tag="ul" class="todo-list">
      <li v-for="todo in filteredTodos" :key="todo.id" class="todo-item">
        <input type="checkbox" v-model="todo.done" />
        <span :class="{ done: todo.done }">{{ todo.id }}. {{ todo.text }}</span>
        <button class="remove-btn" @click="removeTodo(todo)">❌</button>
      </li>
    </transition-group>

    <!-- Tombol Toggle untuk Menyembunyikan Tugas Selesai -->
    <button class="toggle-btn" @click="hideCompleted = !hideCompleted">
      {{ hideCompleted ? 'Show all' : 'Hide completed' }}
    </button>
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

.containerr {
  /* display: flex; */
  /* flex-direction: column; */
  /* align-items: center; */
  justify-content: center;
  width: 350px;
  margin: 20px ; /* Tambahkan margin atas agar lebih naik */
  padding: 20px;
  background: white;
  border-radius: 10px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
  position: relative;
  top: 10px; /* Mengangkat elemen ke atas */
}

h2 {
  color: #42b983;
}

form {
  display: flex;
  gap: 10px;
  margin-bottom: 15px;
}

input {
  flex: 1;
  padding: 8px;
  border: 1px solid #ccc;
  border-radius: 5px;
}

button {
  background-color: #42b983;
  color: white;
  border: none;
  padding: 8px 12px;
  font-size: 14px;
  border-radius: 5px;
  cursor: pointer;
  transition: background 0.3s ease-in-out;
}

button:hover {
  background-color: #369b72;
}

/* Daftar Todo */
.todo-list {
  list-style: none;
  padding: 0;
}

.todo-item {
  display: flex;
  justify-content: space-between;
  background: #e3fcef;
  padding: 8px;
  margin-bottom: 5px;
  border-radius: 5px;
}

/* Efek Animasi */
.fade-enter-active, .fade-leave-active {
  transition: all 0.5s ease;
}

.fade-enter-from, .fade-leave-to {
  opacity: 0;
  transform: translateY(-10px);
}
</style>


