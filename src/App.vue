<template>
  <div id="app" class="container border border-primary p-5 d-flex">
    <div class="row m-1 g-2">
      <h1 style="padding-left: 40px;">Calculadora Vue</h1>
      <hr>
      <div class="col-md-3">
        <label for="x">Número 1:</label>
        <input v-model="estado.x" @input="calcularResultado" type="number" class="form-control" id="x">
      </div>

      <div class="col-md-4">
        <label for="operacao">Operação:</label>
        <select v-model="estado.operacao" @change="calcularResultado" class="form-control" id="operacao">
          <option value="soma">+</option>
          <option value="subtracao">-</option>
          <option value="multiplicacao">*</option>
          <option value="divisao">/</option>
        </select>
      </div>

      <div class="col-md-4">
        <label for="y">Número 2:</label>
        <input v-model="estado.y" @input="calcularResultado" type="number" class="form-control" id="y">
      </div>
      <div class="pt-4">
        <strong>Resultado:</strong> {{ estado.resultado }}
      </div>
    </div>    
  </div>
</template>

<script setup>
import { reactive } from 'vue';

const estado = reactive({
  x: 0,
  y: 0,
  operacao: 'soma',
  resultado: 0
})

const calcularResultado = () => {
  switch (estado.operacao) {
    case 'soma':
      estado.resultado = estado.x + estado.y;
      break;
    case 'subtracao':
      estado.resultado = estado.x - estado.y;
      break;
    case 'multiplicacao':
      estado.resultado = estado.x * estado.y;
      break;
    case 'divisao':
      estado.resultado = estado.x / estado.y;
      break;
    default:
      estado.resultado = 0;
  }
}
</script>

<style>
body {background-color: grey}
.container {
    background-color: white; 
    position: fixed;
    top: 50%;
    left: 50%;
    height: 400px;
    width: 500px;
    -webkit-transform: translate(-50%, -50%);
    transform: translate(-50%, -50%);
}
</style>
