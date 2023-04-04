<script setup>
import { ref,computed } from 'vue';
const url = 'https://animechan.vercel.app/api/available/anime';

const listadoNames = ref([]);
var inicio=0;
var limitacion = 10;
var dormir = ref(false);

const consultaApi = async(init,limit) => {
    try{
        fetch(url).then(response => response.json()).then(data => {
    listadoNames.value = data;
    listadoNames.value = listadoNames.value.slice(init,limit);
    }).catch(e => console.log(e));
    } catch{

    }
    
}
consultaApi(inicio,limitacion);


const siguiente = () => {
    inicio+=10;
    limitacion+=10;
    consultaApi(inicio,limitacion);
    dormir.value =true;
    
}
const anterior = () => {
    inicio-=10;
    limitacion-=10;
    consultaApi(inicio,limitacion);
}

/*para la api puedo guardar la lista completa y reasignar dependiendo de el requisito deseado un rengo de consulta y con este darle las limitaciones*/

</script>

<template>

    <div>
        <h1>Consuminedo apis</h1>
        <button :disabled="!dormir" @click="anterior">atras</button>
        <button @click="siguiente">siguiente</button>
        <ul>
            <li v-for="(x,index) in listadoNames" :key="index">
                {{ index }} - {{ x }}
            </li>
        </ul>
    </div>

</template>

<style scoped>
li{
    list-style: none;
}
</style>