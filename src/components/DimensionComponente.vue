<template>
  <div class="dimension-container">
    <h2>Dimensiones del Componente</h2>
    <p>Ancho: {{ width }}px</p>
    <p>Alto: {{ height }}px</p>
  </div>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue';

const width = ref(0);
const height = ref(0);

const actualizarDimensiones = () => {
  width.value = window.innerWidth;
  height.value = window.innerHeight;
};

onMounted(() => {
  actualizarDimensiones();
  window.addEventListener('resize', actualizarDimensiones);
});

onUnmounted(() => {
  window.removeEventListener('resize', actualizarDimensiones);
});
</script>

<style scoped>
.dimension-container {
  background: rgb(70, 69, 69);
  padding: 1.5rem;
  border-radius: 16px;
  box-shadow: 0 4px 16px rgba(0, 0, 0, 0.1);
  transition: transform 0.2s ease;
  text-align: center;
  width: 100%;
  max-width: 300px;
  margin: 1rem auto;
}
.dimension-container:hover {
  transform: scale(1.03);
}
</style>