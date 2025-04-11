<script setup lang="ts">
 import { ref, watch } from 'vue';

 const value1 = ref<number>(0);
 const value2 = ref<number>(0);
 const operation = ref<string>('sum');
 const result = ref<number | null>(null);

 const calculate = () => {
  switch (operation.value) {
   case 'sum':
    result.value = value1.value + value2.value;
    break;
   case 'sub':
    result.value = value1.value - value2.value;
    break;
   case 'mul':
    result.value = value1.value * value2.value;
    break;
   case 'div':
    result.value = value2.value !== 0 ? value1.value / value2.value : null;
    break;
   default:
    result.value = null;
  }
 };

 watch([value1, value2, operation], calculate);
</script>

<template>
 <div class="container text-center">
  <header>
   <h1 class="mt-1">
   Calculadora Aritmética
  </h1>
  </header>
  <main class="d-flex justify-content-center">
   <input type="number" v-model="value1" class="text-center">
   <select v-model="operation" class="mx-1">
    <option value="sum">
     +
    </option>
    <option value="sub">
     -
    </option>
    <option value="mul">
     *
    </option>
    <option value="div">
     /
    </option>
   </select>
   <input type="number" v-model="value2" class="text-center">
   <span class="mx-1">
    =
   </span>
   <div class="result text-center">
    <p>
     <span>
      {{ result }}
     </span>
    </p>
   </div>
  </main>
  <footer>
   <p class="text-muted mt-2">
    Feito no módulo 27 do curso "Desenvolvedor Full Stack Java v2". &copy; 2025 Leandro A. Mello. No rights reserved.
   </p>
  </footer>
 </div>
</template>

<style scoped>
 .result {
  border: 1px solid #8f8f9d;
  border-radius: 2px;
  width: 200px;
  height: 30px;
 }
</style>
