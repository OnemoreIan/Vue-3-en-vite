<script setup>
//importaciones
import { ref,computed } from 'vue';

/* ------------------------------------------------- */
//variables
var listaEjemplo = ref([]);
var elemento = ref();
var edicion = ref();
var editValue = ref();
var editValue2 = ref();
var desabdled = ref(false);

//funciones
const add = () => {
    listaEjemplo.value.push(elemento.value);
    elemento.value = '';
};
const borrar = (num) => {
    listaEjemplo.value.splice(num,1);
}
const editar = (id) => {
    editValue.value = listaEjemplo.value[id];
    console.log(editValue.value)
    edicion.value = true;
    desabdled.value = true;
}
const guardarCambios = () => {
    let temporl = listaEjemplo.value.indexOf(editValue.value);
    console.log(temporl);
    listaEjemplo.value[temporl] = editValue2.value;
    editValue2.value = '';
    edicion.value = false;
    desabdled.value =false;
}
const cancelar = () => {
    edicion.value = false;
    desabdled.value = false
}

</script>

<template>

    <div class="container">
        <h2>Ejemplo de crud con Vue 3 en vite</h2>
    </div>

    <div class="container">

        <h3>Ingreso de datos</h3>

        <section class="sect">
            <p>Lista de asistencia 2023</p>
            <div>
                <label for="entrada">Ingresa el nombre de quien asiste: </label>
                <input type="text" id="entrada" v-model="elemento" placeholder="Aqui va el nombre">
                <button type="button" @click="add">Guardar</button>
            </div>
        </section>

    </div>

    <div class="container store_edit" v-show="listaEjemplo">

        <section class="sect" >
            <h3>Datos guardados</h3>
            <table class="table">
                <thead>
                    <th>Lista de asistencia carnabal 2023</th>
                </thead>
                <tbody>
                    <tr v-for="(i,index) in listaEjemplo">
                        <td> <span>{{ index+1 }} - {{ i }} </span>  <span class="controles"><button class="click" @click="borrar(index)">Borrar</button>
                            <button class="btn" @click="editar(index)" :disabled="desabdled">Editar</button></span></td>
                    </tr>
                </tbody>
            </table>
        </section>

        <section class="sect" v-show="edicion">
            <h3>Edicion de datos</h3>
            <div class="editPanel">
                <label for="">Edita el nombre</label>
                <input type="text" v-model="editValue2" :placeholder="editValue">
                <div>
                    <button class="click" @click="guardarCambios">Guardar</button><button class="btn" @click="cancelar">Cancelar</button>
                </div>
            </div>
            
        </section>

    </div>

</template>

<style scoped>
.container{
    margin: 1rem;
    padding: .5rem 1rem;
    color: lightskyblue;
}

.sect{
    margin: 1.5rem 0;
}
.editPanel{
    display: grid;
    justify-content: center;
    align-content: center;
}
.table{
    margin: 0 auto;
    border-collapse: collapse;
    outline: 1px solid rgb(188, 188, 188);
}
th,td{
    padding: .3rem .8rem;
    outline: 1px solid rgb(188, 188, 188);
}
td{
    text-align: center;
    display: flex;
    flex-flow: row nowrap;
     justify-content: space-between;
}
.controles{
    display: flex;
    gap: 1rem;
}
h2{
    text-align: center;
}
</style>