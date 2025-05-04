<template>
  <div class="lista-container">
    <h2>Lista de Profesionales</h2>
    <ul v-if="profesionales.length > 0">
      <li v-for="profesional in profesionales" :key="profesional.id">
        <strong>{{ profesional.nombre }}</strong>: {{ profesional.descripcion }}
      </li>
    </ul>
    <p v-else class="cargando">Cargando profesionales...</p>
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue';
import { profesiones } from '../resource/profesiones.ts';

const profesionales = ref([]);

onMounted(() => {
  setTimeout(() => {
    profesionales.value = profesiones;
  }, 3000);
});
</script>

<style scoped>
.list-container {
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


h2 {
  color: darkgoldenrod;
  margin-bottom: 15px;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
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
li:hover {
  transform: scale(1.03);
}
li strong {
  color: darkgoldenrod;
}

.cargando {
  text-align: center;
  padding: 20px;
  color: darkgoldenrod;
  font-style: italic;
}
</style>