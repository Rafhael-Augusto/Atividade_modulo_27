<script setup>
const props = defineProps(['NumerosObj'])
</script>

<template>
    <div class="Simbulos">
        <select
            @change="evento => { NumerosObj.Simbulo = evento.target.value, NumerosObj.NumeroDisplay = '0', NumerosObj.numeroA = '', NumerosObj.numeroB = '' }">
            <option value="+">+</option>
            <option value="-">-</option>
            <option value="*">x</option>
            <option value="/">/</option>
        </select>
    </div>
</template>

<style scoped>
.Simbulos {
    display: flex;
    justify-content: center;
    padding: 50px 0;
}

select {
    text-align: center;
}
</style>