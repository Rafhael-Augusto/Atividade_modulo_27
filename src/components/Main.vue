<script setup>
const props = defineProps(['NumerosObj', 'CalcularFunc'])
</script>

<template>
    <div class="Main">
        <div class="Numbers">
            <input :value="NumerosObj.numeroA" @keyup="evento => CalcularFunc(evento.target.value, 'A')" type="number"
                placeholder="0">
            <input :value="NumerosObj.numeroB" @keyup="evento => CalcularFunc(evento.target.value, 'B')" type="number"
                placeholder="0">
        </div>
        <div class="Reslt">
            <h2>{{ NumerosObj.NumeroDisplay }}</h2>
        </div>
    </div>
</template>

<style scoped>

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