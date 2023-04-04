<script setup>
import { ref } from 'vue';
  const ejemploVar1 = '-Voy la variable-';
  const condicionIf = true;
  const labelBotones = ref('');
  const listaL = ['domino', 'deadpool', 'lobezno', 'juguernaut'];
  const alist = [
    {"id": 'elemento', num: 1,relleno: 'nansnas9'},
    {"id": 'elemento2',num: 2,relleno: 'nansnas8'},
    {"id": 'elemento4',num: 3,relleno: 'nansnas7'},
    {"id": 'elemento6',num: 4,relleno: 'nansnas6'},
    {"id": 'elemento8',num: 5,relleno: 'nansnas5'},
    {"id": 'elemento10',num: 6,relleno: 'nansnas1'}
  ]
  const listaCompleja = [{id: 1,num: 1,relleno: {id: 1,base2: {id: 1,elem: [1, 2, 3, 4]}}},
    {id: 2,num: 2,relleno: {id: 2,base2: {id: 2,elem: [1, 2, 3, 4]}}},
    {id: 3,num: 3,relleno: {id: 3,base2: {id: 3,elem: [1, 2, 3, 4]}}},
    {id: 4,num: 4,relleno: {id: 4,base2: {id: 4,elem: [1, 2, 3, 4]}}},
    {id: 5,num: 5,relleno: {id: 5,base2: {id: 5,elem: [1, 2, 3, 4]}}},
    {id: 6,num: 6,relleno: {id: 6,base2: {id: 6,elem: [1, 2, 3, 4]}}},
  ]
  const frutas = {
    nombre: 'manzana',
    precio: 1.5,
    descripcion: 'manzana roja',
    id: 1
  }
  const soyUnBoton = mens => {
    labelBotones.value = mens;
  } 
</script>

<template>
  <main class="space">

    <div class="container">
      <h1>Aprendisaje express de Vue en vite</h1>
    </div>

    <div class="container">
      <h2>Variables dentro del html</h2>
      <p>Aqui estoy usando una variable => {{ ejemploVar1 }}</p>
      <p>usar una variable es igual que en Angular</p>
    </div>

    <div class="container">
      <h3>Condiciones con if</h3>
      <p>Para la mayoria de directivas se usa v-if,for...,<br>Las propiedades aceptas comparaciones de texto y multiples condiciones,<br>Con la condicion que si una estiquta tiene el v-if la siguiente debe de contener,</p>
      <p>v-else-if, no obligatoriamente la siguiente linea, sino que la siguiente etiqueta,<br>Dentro del mismo padre. Para finalizar tambien puedes usar else como ultima opcion.</p>
      <p v-if="condicionIf">Soy la opcion 1</p>
      <p v-else-if="condicionIf">Soy la opcion 2</p>
      <h5 v-else-if="condicionIf">Soy la opcion 3</h5>
      <h1 v-else>Soy la ultima opcion</h1>
    </div>

    <div class="container">
      <h3>Renderizado con for</h3>
      <p>La sintaxis de for es similar v-for y se parece a la de angular al momento de declarada<br>La diferencia principal es el hecho de uso de index</p>

    </div>
    <div class="container">

      <p>Lista</p>
      <ul class="ul">
        <li class="li" v-for="x in listaL"> <span v-if="index === 0">index - {{ index+1 }} </span> {{ x }}</li>
      </ul>

    </div>
    <div class="container">

      <p>Objeto</p>
      <ul class="ul">
        <li class="li" v-for="(x,i) in alist" :key="x.id"> <span>Id {{ x.id }} numero {{ x.num }} relleno {{ x.relleno }} Indice {{ i+1 }} </span> </li>
      </ul>

    </div>
    <div class="container">

      <p>Lista de Objetos</p>
      <ul class="ul">
        <li class="li" v-for="(value,propiedad,index) in frutas" :key="value.id"> {{ index+1 }} - {{ propiedad }} - {{ value }} </li>
      </ul>

    </div>

    <div class="container">

      <h3>Acciones con clicks</h3>
      <p>El uso de funciones con click es simple, solo se aplica una propiedad @click="nombre de funcion"<br>Similar en otros framework</p>
      <button @click="soyUnBoton('Soy el botn de la Izquierda')">Dame un click</button>
      <button @click="soyUnBoton('Soy el botn de la Derecha')">Dame un click</button>
      <p>{{ labelBotones }}</p>

    </div>

  </main>
    
</template>

<style scoped>
.space{
  width: 100%;
}
.container{
  margin: 1rem;
  color: lightskyblue;
  padding: .5rem 1rem;
}
.ul li{
  list-style: none;
}
button{
  color: black;
}
h1 {
    text-align: center;
    color: white;
    font-size: 2rem;
}
h2,h3,h4{
  color: white;
}
</style>