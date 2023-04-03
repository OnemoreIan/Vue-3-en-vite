<script setup>
//importaciones
import { ref,computed } from 'vue';

//ejercicio
//variables
var listaEjemplo = ref([]);
var elemento = ref('');

//funciones
const add = () => {
    listaEjemplo.value.push(elemento.value);
    elemento.value = '';
};
const borrar = (num) => {
    listaEjemplo.value.splice(num,1);
}

</script>

<template>

    <div class="espacio">
        <h1>Ejemplo de crud con Vue</h1>
        <h2>Lista de acistencia 2023</h2>

        <section class="sect">
            <h2>Entrada de datos</h2>
            <div>
                <form>
                    <label for="entrada">Ingresa un nombre: </label>
                    <input type="text" id="entrada" v-model="elemento" placeholder="Ingresa un nombre">
                    <button type="button" @click="add()">Aceptar</button>
                </form>
            </div>
        </section>

        <section class="sect">
            <h2>Muestra datos</h2>
            <table class="table">
                <thead>
                    <th>Lista de asistencia carnabal 2023</th>
                </thead>
                <tbody>
                    <tr v-for="(i,index) in listaEjemplo">
                        <td> {{ index+1 }} .- {{ i }}   <button @click="borrar(index)">Borrar</button>
                        </td>
                            
                    </tr>

                </tbody>
            </table>
        </section>

    </div>

</template>

<style scoped>
.espacio{
    min-width: 500px;
    min-height: 700px;
    background-color: chocolate;
    color: black;
    font-family: 'Franklin Gothic Medium', 'Arial Narrow', Arial, sans-serif;
}
.sect{
    margin: 1.5rem 0;
}
.table{
    border: 2px solid black;
}
.table>thead>th{
    border-bottom: 2px solid black;
}
</style>