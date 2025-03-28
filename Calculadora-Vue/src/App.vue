<template>
  <div class="container mt-5">
    <div class="row justify-content-center">
      <div class="col-md-9">
        <div class="card shadow">
          <div class="card-header bg-primary text-white">
            <h2 class="mb-0">Calculadora Vue.js</h2>
          </div>

          <div class="card-body">
            <div class="mb-3">
              <input 
                type="number" 
                v-model="num1" 
                placeholder="Digite o primeiro número"
                class="form-control form-control-lg"
              >
            </div>

            <div class="mb-3">
              <input 
                type="number" 
                v-model="num2" 
                placeholder="Digite o segundo número"
                class="form-control form-control-lg"
              >
            </div>

            <!-- Seleção para culculo  das operação -->
            <div class="mb-3">
              <select 
                v-model="operacao" 
                class="form-select form-select-lg"
              >
                <option value="soma">+ Adição</option>
                <option value="subtracao">- Subtração</option>
                <option value="multiplicacao">× Multiplicação</option>
                <option value="divisao">÷ Divisão</option>
              </select>
            </div>
            <!-- Botão para calcular -->
             
            <div class="alert alert-info fs-4">
              <strong>Resultado:</strong> {{ resultado }}
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, computed } from 'vue';

const num1 = ref(0);
const num2 = ref(0);
const operacao = ref('soma');

const resultado = computed(() => {
  const a = parseFloat(num1.value);
  const b = parseFloat(num2.value);

  switch (operacao.value) {
    case 'soma':
      return a + b;
    case 'subtracao':
      return a - b;
    case 'multiplicacao':
      return a * b;
    case 'divisao':
      return b !== 0 ? (a / b).toFixed(2) : 'Erro: divisão por zero';
    default:
      return 0;
  }
});
</script>

<style scoped>
.card {
  border-radius: 15px;
}

.form-control-lg, .form-select-lg {
  font-size: 1.25rem;
}
</style>