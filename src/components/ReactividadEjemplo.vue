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
    if(comprobacion === 0){
        return true
    }
    return comprobacion ? true : false
})


const test = () => {
    alert('xxxx');
}
</script>

<template>

<main class="space">
    <div class="container">
        <h2>Reactividad</h2>
    </div>
    <div class="container">
        <p>En Vue puedes pasar funciones o variables como parametros<br>Pero se debe de tener encuenta unos aspectos</p>
        <p>Para la reactividad se utiliza unas librerias que se deben de importar desde Vue<br>En la parte de Js usas la importacion:  import { ref,computed } from 'vue'</p>
        <p>Con las importaciones puedes hacer que las variables y funciones sean escuchadas<br>En el caso de las variables *de todo tipo  encierras el valor en ref(aqui va el valor de la variable)</p>
        <p>En el caso de las funciones deberas de encerrar el contenido en la propiedad computed y siempre debe returnar algo<br>var local = ref(valor) ||||  const miFuncion = computed(() => {aqui va el codigo a ejecutar y un return})</p>
        <p>No confundir de usar funciones normales y funciones reactivas ya que da error<br>Para que los botones ejecuten funciones son funciones sin el computed</p>        
        
    </div>
    <div class="container">
        <h4>Caja reactiva al valor</h4>
        <div class="colorSpace">
            <p :class="claseStyle"> clicks => {{ count }}</p>
        </div>
        <div class="controlButton">
            <button @click="inrementador">sumar </button>
            <button @click="decrementador">restar</button>
            <button @click="reiniciar">Resetear</button>
            
            <button :disabled="busqueda" @click="gusto">Agregar</button>
        </div>
        <p class="advertecia" v-show="busqueda">Para agregar un numero no debe de estar repetido</p>

        <div class="listaInvisible" v-show="listaProyecto">
            <h3>Reactividad de elementos</h3>
            <p>Lista de numeros favoritos</p>
            
            <ul>
                <li v-for="i in listaProyecto"> {{ i }} </li>
            </ul>
        </div>
    </div>

    <div class="container">
        <h3>Agregar elementos en tiempo real</h3>
        <div class="formulario">
            <input type="text"  v-model="dato" minlength="1" placeholder="Ingresa un nombre">
            <button type="button" @click="add">agregar</button>
        </div>

        <div class="espacioTabla">
            <table class="tabla">
                <thead>
                    <th>
                        Nombre
                    </th>
                </thead>
                <tbody>
                    <tr v-for="item in Megalista">
                        <td>{{ item }}</td>
                    </tr>
                </tbody>
            </table>
        </div>
        
    </div>
</main>



</template>



<style scoped>
.container{
    margin: 1rem;
    padding: .5rem 1rem;
    color: lightskyblue;
}
.colorSpace{
    background-color: black;
    width: fit-content;
    height: fit-content;
    padding: 1rem 2rem;
    border-radius: 3rem;
    margin: 0 auto;
}
.advertecia{
    text-align: center;
    color: yellow;
    padding: .5rem 0;
}
.controlButton{
    padding: 1rem 0;
    display: flex;
    flex-flow: row wrap;
    justify-content: center;
    gap: 1rem;
}
.listaInvisible{
    display: flex;
    flex-flow: column nowrap;
    align-items: center;
}
.formulario,.espacioTabla{
    margin: 1rem 0;
    display: flex;
    justify-content: center;
}
.tabla{
    box-sizing: border-box;
    border: 1px solid whitesmoke;
}
.tabla thead th{
    border: 1px solid whitesmoke;
}
.tabla tbody tr{
    border: 1px solid whitesmoke;
}
.error{
    color: red;
}
.exito{
    color: rgb(0, 255, 38);
}
.cero{
    color: red;
    animation: multicolor .7s infinite both;
}
/*hasta aqui */
@keyframes multicolor {
    20%{color: rgb(255, 247, 0);}
    40%{color: rgb(26, 255, 0);}
    60%{color: rgb(0, 242, 255);}
    80%{color: rgb(13, 0, 255);}
    100%{color: rgb(255, 0, 217);}
}
h2{
    text-align: center;
}
</style>