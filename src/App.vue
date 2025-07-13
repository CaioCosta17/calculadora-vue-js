<script setup>
  import { ref, computed } from 'vue';

  const numero1 = ref(0);
  const numero2 = ref(0);
  const operacao = ref('+'); // Valor inicial da operação 

  const resultado = computed(() => {
    const num1 = parseFloat(numero1.value); // Converte para número
    const num2 = parseFloat(numero2.value);

    if (isNaN(num1) || isNaN(num2)) {
      return 'Entrada inválida';
    }

    switch (operacao.value) {
    case '+':
      return num1 + num2;
    case '-':
      return num1 - num2;
    case '*':
      return num1 * num2;
    case '/':
        if (num2 === 0) { // Evita a divisão por 0
        return 'Não pode dividir por zero';
      }
      return num1 / num2;
    default:
      return 0;
    }
  })
</script>

<template>
  <div id="app" class="d-flex justify-content-center align-items-center min-vh-100 bg-dark">
    <div class="card p-4" style="width: 28rem;">
      <h2 class="card-title text-center mb-4 fw-bold">Calculadora Aritmétrica</h2>
      <div class="mb-3">
        <label for="numero1" class="form-label fw-bold">Primeiro Número:</label>
        <input
          type="number"
          id="numero1"
          class="form-control"
          v-model.number="numero1"
          placeholder="Digite o primeiro número"
        />
      </div>
      <div class="mb-3">
        <label for="numero2" class="form-label fw-bold">Segundo Número:</label>
        <input
          type="number"
          id="numero2"
          class="form-control"
          v-model.number="numero2"
          placeholder="Digite o segundo número"
        />
      </div>
      <div class="mb-4">
        <label for="operacao" class="form-label fw-bold">Operação:</label>
        <select id="operacao" class="form-select" v-model="operacao">
          <option value="+">Adição (+)</option>
          <option value="-">Subtração (-)</option>
          <option value="*">Multiplicação (x)</option>
          <option value="/">Divisão (/)</option>
        </select>
      </div>
      <div class="alert alert-success text-center h4" role="alert">
        Resultado: <span class="fw-bold">{{ resultado }}</span>
      </div>
    </div>
  </div>
</template>