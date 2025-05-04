<template>
  <div class="tareas-container">
    <h2>Administrador de Tareas</h2>
    
    <div class="input-group">
      <input
        v-model="nuevaTarea"
        @keyup.enter="agregarTarea"
        placeholder="Nueva tarea"
      >
      <button @click="agregarTarea">Agregar</button>
    </div>
    
    <ul class="lista-tareas">
      <li
        v-for="(tarea, index) in tareas"
        :key="index"
        :class="{'tarea-existente': esTareaAntigua(tarea)}"
      >
        {{ tarea }}
      </li>
    </ul>
  </div>
</template>

<script setup>
import { ref, onBeforeUpdate, onUpdated } from 'vue';

const tareas = ref(['Hacer TP de Vue', 'Estudiar lifecycle hooks', 'Revisar documentación']);
const nuevaTarea = ref('');
const tareasAntesDeModificar = ref([]);

const agregarTarea = () => {
  if (nuevaTarea.value.trim()) {
    tareasAntesDeModificar.value = [...tareas.value];
    tareas.value.push(nuevaTarea.value.trim());
    nuevaTarea.value = '';
  }
};

const esTareaAntigua = (tarea) => {
  return tareasAntesDeModificar.value.includes(tarea);
};

onBeforeUpdate(() => {
  console.log("Lista aún no modificada");
});

onUpdated(() => {
  console.log("Lista modificada");
});
</script>

<style scoped>
.tareas-container {
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
.tareas-container:hover {
  transform: scale(1.03);
}

.input-group {
  display: flex;
  margin-bottom: 15px;
}

input {
  background-color: #828381;
  flex-grow: 1;
  padding: 8px;
  margin-right: 10px;
  color: darkgoldenrod;
}

button {
  padding: 8px 15px;
  background-color: #191a19;
  color: darkgoldenrod;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}

.lista-tareas {
  list-style-type: none;
  padding: 0;
}

.lista-tareas li {
  padding: 10px;
  margin: 5px 0;
  border-radius: 4px;
}

.tarea-existente {
  background-color: #0a0a0a;
  border-left: 4px solid #4a4b4a;
}

.lista-tareas li:not(.tarea-existente) {
  background-color: #4a4b4a;
  border-left: 4px solid #0a0a0a;
}
</style>