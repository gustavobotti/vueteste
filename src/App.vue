<template>
  <div id="app" class="container border border-primary p-5 d-flex">
    <div class="row m-1 g-2">
      <h1 style="padding-left: 40px;">Calculadora Vue</h1>
      <hr>
      <div class="col-md-3">
        <label for="x">Número 1:</label>
        <input v-model="x" @input="calcularResultado" type="number" class="form-control" id="x">
      </div>

      <div class="col-md-4">
        <label for="operacao">Operação:</label>
        <select v-model="operacao" @change="calcularResultado" class="form-control" id="operacao">
          <option value="soma">+</option>
          <option value="subtracao">-</option>
          <option value="multiplicacao">*</option>
          <option value="divisao">/</option>
        </select>
      </div>

      <div class="col-md-4">
        <label for="y">Número 2:</label>
        <input v-model="y" @input="calcularResultado" type="number" class="form-control" id="y">
      </div>
      <div class="pt-4">
        <strong>Resultado:</strong> {{ resultado }}
      </div>
    </div>    
  </div>
</template>

<script>
export default {
  data() {
    return {
      x: 0,
      y: 0,
      operacao: 'soma',
      resultado: 0
    };
  },
  methods: {
    calcularResultado() {
      switch (this.operacao) {
        case 'soma':
          this.resultado = this.x + this.y;
          break;
        case 'subtracao':
          this.resultado = this.x - this.y;
          break;
        case 'multiplicacao':
          this.resultado = this.x * this.y;
          break;
        case 'divisao':
          this.resultado = this.x / this.y;
          break;
        default:
          this.resultado = 0;
      }
    }
  }
};
</script>

<style>
@import "./node_modules/bootstrap/dist/css/bootstrap.min.css";
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
