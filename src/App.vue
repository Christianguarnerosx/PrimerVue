//Logica
<script setup>
//importamos la reactividad
import { ref, computed } from 'vue'

const name = 'Vue Dinamico';

/*Variable recativa. Se puede utilizar valores primitivos (ints,string,etc) u objetos, arrays, etc*/
const contador = ref(0);

const incrementar = () => {
    contador.value++; //Si utilizamos la reactividad ref siempre se hace referencia al value de la variable/dato
}

const disminuir = () => {
    contador.value--
}

const reiniciar = () => {
    contador.value = 0
}


/* Siempre tratar de usar esta opcion de propiedades computadas */
const vericontador = computed(() => { //propiedad computada/calculada (se almacena en la cache) (obligatorio el return)
    if (contador.value == 0) {
        return 'neutro' //mandamos esta clase css
    } else if (contador.value <= 0) {
        return 'desactivo' //mandamos esta clase css
    } else {
        return 'activo' //mandamos esta clase css
    }
})

//Tambien se puede como metodo/funcion (obligatorio el return) 2da opcion
/*const verificarcontador = () => {
    if (contador.value == 0) {
        return 'neutro' //mandamos esta clase css
    } else if (contador.value <= 0) {
        return 'desactivo' //mandamos esta clase css
    } else {
        return 'activo' //mandamos esta clase css
    }
}*/

let arrayfav = ref([]);

const agregarfav = () => {
    arrayfav.value.push(contador.value)
}

const verifiarray = computed(() => {
    const numbuscar = arrayfav.value.find(num => num === contador.value);
    console.log(numbuscar);
    if (numbuscar === 0) {
        return true
    }
    return numbuscar ? true : false;
})
</script>


//Estructura
//(template obligatorio)
<template>
    <div class="text-center">
        <h1>Hola {{ name.toUpperCase() }}</h1>
        <!-- Se renderiza con la reactividad solo el h2 que es reactivo (ref) -->
        <h2 :class="vericontador">{{ contador }}</h2>
        <!--<h2 :class="verificarcontador()">{{ contador }}</h2>  opcion con metod/function normal en js-->
        <div>
            <button @click="incrementar"
                class="bg-blue-500 hover:bg-blue-400 text-white font-bold py-2 px-4 border-b-4 border-blue-700 hover:border-blue-500 rounded">Aumentar</button>
            <button @click="disminuir"
                class="bg-blue-500 hover:bg-blue-400 text-white font-bold py-2 px-4 border-b-4 border-blue-700 hover:border-blue-500 rounded">Disminuir</button>
            <button v-on:click="reiniciar"
                class="bg-blue-500 hover:bg-blue-400 text-white font-bold py-2 px-4 border-b-4 border-blue-700 hover:border-blue-500 rounded">Reiniciar</button>
            <button @click="agregarfav" :disabled="verifiarray"
                class="bg-blue-500 hover:bg-blue-400 text-white font-bold py-2 px-4 border-b-4 border-blue-700 hover:border-blue-500 rounded">Favoritos</button>
        </div>

        <ul>
            <li v-for="(numero, index) in arrayfav" :key="index"> {{ numero }}</li>
        </ul>
    </div>

</template>


//Estilos
<style>
.activo{
    color: green;
}

.desactivo{
    color: red;
}

.neutro{
    color: steelblue;
}

h1{
    color: rgb(17, 179, 141);
}

</style>