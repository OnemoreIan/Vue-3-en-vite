<script setup>
import { ref,computed } from 'vue';
const actividad = () => {
    console.log('Funcionamiento optimo');
}
const count = ref(0);
const inrementador = () => count.value ++;
const decrementador = () => count.value --;
const reiniciar = () => count.value = 0;

const Megalista = ref(['Pablo','Juan']);

var dato = ref('');
const add = () => {
    Megalista.value.push(dato.value);
    dato.value = '';
}

//estilos reactivos

const claseStyle = computed(() => {
    if(count.value === 0){return 'cero'}
    if(count.value >= 1){return 'exito'}
    return 'error'
})


//mini proyecto de lista
var listaProyecto = ref([]);

const gusto = () => {
    listaProyecto.value.push(count.value);
    count.value=0;
}
const busqueda = computed(() => {
    let comprobacion = listaProyecto.value.find(num => num == count.value)
    console.log(comprobacion);
    if(comprobacion === 0){return true}
    return comprobacion ? true : false
})

</script>

<template>

    <div>
        <h1>Reactividad</h1>
        <p :class="claseStyle"> clicks => {{ count }}</p>
        <button @click="inrementador">sumar </button>
        <button @click="decrementador">restar</button>
        <button @click="reiniciar">Resetear</button>
        <span v-show="busqueda">El numero ya existe  </span>
        <button v-show="!busqueda" @click="gusto">Agregar</button>

        <div v-show="listaProyecto">
            <h2>numeros favorito</h2>
            <ul>
                <li v-for="i in listaProyecto"> {{ i }} </li>
            </ul>
        </div>
    </div>
    <div>
        <h1>reactividad con listas</h1>
        <input type="text" v-model="dato" minlength="1" placeholder="Ingresa un nombre">
        <button @click="add()">agregar</button>
        <ul>
            <li v-for="item in Megalista"> {{ item }} </li>
        </ul>
    </div>

</template>



<style scoped>
.error{
    color: red;
}
.exito{
    color: rgb(0, 255, 38);
}
.cero{
    color: yellow;
    animation: multicolor 1s infinite;
}
@keyframes multicolor {
    17%{color: rgb(255, 0, 0);}
    34%{color: rgb(255, 247, 0);}
    51%{color: rgb(26, 255, 0);}
    68%{color: rgb(0, 242, 255);}
    85%{color: rgb(13, 0, 255);}
    100%{color: rgb(255, 0, 217);}
}

</style>