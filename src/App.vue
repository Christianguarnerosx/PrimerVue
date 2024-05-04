/* Single file component */
//Logica
<script setup>
const name = 'Vue Dinamico';

//metodo - methods

const hacerclick = (mensaje) =>{
    console.log(mensaje)
}
</script>

//Estructura
//(template obligatorio)
<template>
    <!-- Bien, lo que vemos es -->
<button v-on:click="hacerclick('Hola opresor 1')">Presioname</button>
<button @:click="hacerclick('Hola crack 2')">Presioname 2</button>
</template>

//Estilos
<style>
h1{
    color: red;
}
</style>