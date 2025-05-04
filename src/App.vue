<template>
  <div class="app-container">
    <h1>Trabajo Práctico N°4 - Ciclo de vida</h1>
    
    <div class="selector-container">
      <label>Seleccione un componente: </label>
      <select v-model="componenteActual">
        <option value="Tareas">Tareas</option>
        <option value="Lista">Lista</option>
        <option value="DimensionComponente">Dimensiones</option>
      </select>
    </div>
    
    <div class="componente-activo">
      <component :is="componenteSeleccionado" />
    </div>
  </div>
</template>

<script setup>
import { ref, computed } from 'vue';
import Tareas from './components/Tareas.vue';
import Lista from './components/Lista.vue';
import DimensionComponente from './components/DimensionComponente.vue';

const componenteActual = ref('Tareas');

const componentes = {
  Tareas,
  Lista,
  DimensionComponente
};

const componenteSeleccionado = computed(() => {
  return componentes[componenteActual.value];
});
</script>

<style>
.app-container {
  font-family: 'Segoe UI', sans-serif;
  background-color: #777272;
  min-height: 100vh;
  text-align: center;
  color: darkgoldenrod;
  padding: 20px;
  display: flex;
  flex-direction: column;
  width: 100%;
  margin: auto;
  transform: scale(1.01);
}

.selector-container {
  background: rgb(70, 69, 69);
  padding: 1.5rem;
  border-radius: 16px;
  box-shadow: 0 4px 16px rgba(0, 0, 0, 0.1);
  transition: transform 0.2s ease;
  color: darkgoldenrod;
  text-align: center;
  width: 100%;
  max-width: 300px;
  margin: 1.5rem auto;
}

select {
  background-color: #2b2929;
  text-align: center;
  color: darkgoldenrod;
  padding: 5px;
  margin-top: 10px;
}

.componente-activo {
   margin-top: 20px;
  padding: 20px;
  }
</style>