/* Single file component */
//Logica
<script setup>
const name = 'Vue Dinamico';

//metodo - methods

const hacerclick = (mensaje) => {
    console.log(mensaje)
}
</script>

//Estructura
//(template obligatorio)
<template>
    <button @:click="hacerclick('Hola crack 2')">Presioname crack</button>
    <button @:click="hacerclick('Opresorrrrr')">Presioname opresor</button>
    <button @:click.right="hacerclick('Opresorrrrr')">Presioname opresor derecho</button>
    <button v-on:click.right.prevent="hacerclick('Opresorrrrr')">Presioname opresor derecho sin opciones</button>
    <button v-on:click.middle="hacerclick('Opresorrrrr')">Presioname opresor de en medio</button>
</template>

//Estilos
<style>
h1{
    color: red;
}
</style>