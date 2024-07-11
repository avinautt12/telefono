<script setup>
import { ref } from 'vue';

const titulo = "Registro de Teléfonos";
const nombre = "Nombre:";
const numero = "Número de Teléfono:";

const arrayTelefonos = ref([]);

const nombreInput = ref('');
const numeroInput = ref('');

const agregar = () => {
  const nombre = nombreInput.value.trim();
  const numero = numeroInput.value.trim();

  if (nombre === '' || numero === '') {
    alert('Debes llenar ambos campos antes de agregar el contacto.');
    return;
  }
  if (numero.length !== 10) {
    alert('El número debe tener 10 dígitos.');
    return;
  }

  arrayTelefonos.value.push({ nombre: nombre, numero: numero});
  limpiarCampos();
};

const limpiarCampos = () => {
  nombreInput.value = '';
  numeroInput.value = '';
};
</script>

<template>
  <h1>{{ titulo }}</h1>
  <div class="contenedor">
    <div class="item">
      <h2>{{ nombre }}</h2>
      <input type="text" v-model="nombreInput" />
    </div>
    <div class="item">
      <h3>{{ numero }}</h3>
      <input type="text" v-model="numeroInput" />
    </div>
  </div>
  <div style="text-align: center;">
    <button @click="agregar" class="boton">AGREGAR</button>
    <button @click="limpiarCampos" class="boton">LIMPIAR</button>
  </div>
  <br>
  <ul>
    <li v-for="(telefono, index) in arrayTelefonos" :key="index">
      Nombre: {{ telefono.nombre }} -> Número: {{ telefono.numero }}
    </li>
  </ul>
</template>

<style>
h1 {
  display: flex;
  justify-content: center;
  color: black;
  font-family: Arial, Helvetica, sans-serif;
}

h3, h2{
  font-size: 25px;
}

.contenedor {
  display: flex;
  justify-content: space-evenly;
  align-items: center;
  margin-top: 70px;
  font-size: 20px;
  font-family: Arial, Helvetica, sans-serif;
}

.item {
  display: flex;
  align-items: center;
}

h2 {
  margin-right: 0;
}

input {
  padding: 10px;
  font-size: 16px;
  border: 1px solid #ccc;
  border-radius: 4px;
}

.boton{
  font-size: 20px; 
  padding: 5px 15px;
}
</style>
