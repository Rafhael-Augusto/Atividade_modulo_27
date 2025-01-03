<script setup>
import { reactive } from 'vue';
import Principal from './components/Main.vue';
import Simbulos from './components/Simbulos.vue';

const Numeros = reactive({
  numeroA: '',
  numeroB: '',
  NumeroDisplay: '0',
  Simbulo: '+',
})

function Calcular(valor, pos) {
  if (pos === 'A') {
    Numeros.numeroA = valor
  } else {
    Numeros.numeroB = valor
  }
  if (Numeros.numeroA !== '' && Numeros.numeroB !== '') {
    const estrutura = Numeros.numeroA + Numeros.Simbulo + Numeros.numeroB
    const calc = new Function(`return ${estrutura}`)()
    Numeros.NumeroDisplay = calc
  }
}

</script>

<template>
  <h1>Calculadora</h1>
  <div class="Calculadora">

    <Principal :-numeros-obj="Numeros" :-calcular-func="Calcular" />
    <Simbulos :-numeros-obj="Numeros" />
  </div>
</template>

<style scoped>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

.Calculadora {
  display: flex;
  justify-content: center;
}

h1 {
  text-align: center;
}
</style>
