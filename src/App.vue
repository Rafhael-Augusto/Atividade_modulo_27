<script setup>
import { reactive } from 'vue';
  const Numeros = reactive ({
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

    <div class="Main">
      <div class="Numbers">
        <input :value="Numeros.numeroA" @keyup="evento => Calcular(evento.target.value, 'A')" type="number" placeholder="0">
        <input :value="Numeros.numeroB" @keyup="evento => Calcular(evento.target.value, 'B')" type="number" placeholder="0">
      </div>
      <div class="Simbulos">
        <select @change="evento => {Numeros.Simbulo = evento.target.value, Numeros.NumeroDisplay ='0', Numeros.numeroA = '', Numeros.numeroB = ''}">
          <option value="+">+</option>
          <option value="-">-</option>
          <option value="*">x</option>
          <option value="/">/</option>
        </select>
      </div>

      <div class="Reslt">
        <h2>{{ Numeros.NumeroDisplay }}</h2>
      </div>
    </div>
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

.Main {
  padding-top: 35px;
}

input {
  margin: 0 25px;
}

.Simbulos {
  display: flex;
  justify-content: center;
}

h1 {
  text-align: center;
}

.Reslt {
  display: flex;
  justify-content: center;
}

h2 {
  margin-top: 20px;
  text-align: right;
  background-color: gray;
  border-radius: 10px;
  padding: 20px 0;
  width: 200px;
}

</style>
