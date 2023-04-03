<script setup>
const nom = 'Junga';
var dobleVia = '';
var opcion = false;
var cola = 'Juanin';
const listaL = ['domino','deadpool','lobezno','juguernaut'];
const alist = [
  {"id":'elemento',num:1,relleno:'nansnas9'},
  {"id":'elemento2',num:2,relleno:'nansnas8'},
  {"id":'elemento4',num:3,relleno:'nansnas7'},
  {"id":'elemento6',num:4,relleno:'nansnas6'},
  {"id":'elemento8',num:5,relleno:'nansnas5'},
  {"id":'elemento10',num:6,relleno:'nansnas1'},
]
const listaCompleja = [
  {id:1,num:1,relleno:{id:1,base2: {id:1,elem:[1,2,3,4]}}},
  {id:2,num:2,relleno:{id:2,base2: {id:2,elem:[1,2,3,4]}}},
  {id:3,num:3,relleno:{id:3,base2: {id:3,elem:[1,2,3,4]}}},
  {id:4,num:4,relleno:{id:4,base2: {id:4,elem:[1,2,3,4]}}},
  {id:5,num:5,relleno:{id:5,base2: {id:5,elem:[1,2,3,4]}}},
  {id:6,num:6,relleno:{id:6,base2: {id:6,elem:[1,2,3,4]}}},
]
const frutas= {
  nombre:'manzana',
  precio: 1.5,
  descripcion: 'manzana roja',
  id:1
}



const soyUnBoton = mens => {
  console.log(`Boton ${mens}`);
}

</script>

<template>
  <div class="index">
    <h1>Documento plano de vue sin elecciones</h1>
  <h2> Se nos petateo el {{ nom }} -aqui uso interpolacion-</h2>
  <h3 v-bind="dobleVia">Elemento de doble via --aunno definido--</h3>
  <p>aqui uso if</p>
  <h1 v-if="cola == 'Pablo'">Soy la opcion 1</h1>
  <p v-else-if="cola == 'Marta'">Soy la opcion 2</p>
  <h5 v-else-if="cola =='Juanin'">Soy la opcion 3</h5 >
  <h1 v-else>Soy la ultima opcion</h1>
  </div>
  <div>
    <hr>
    <hr>
    <hr>
  </div>
  <div>
    <h1>for con vue</h1>
    <ul>
      <li v-for="(x, index) in listaL" :key="index"> <span v-if="index === 0">index - {{ index+1 }} </span>  {{ x }} </li>
    </ul>
    <div>
      <p>uso de for con objetos</p>
      <ul>
        <li v-for="(x,i) in alist" :key="x.id"> <span>Id {{ x.id }}</span> <span>numero {{ x.num }}</span> <span>relleno {{ x.relleno }}</span> <span>Indice {{ i+1 }} </span> </li>
      </ul>prueba con objeto dentro de otro objeto y usarlo conn for
      <ul>
        <li v-for="(value,propiedad,index) in frutas" :key="value.id"> {{ index+1 }} {{ propiedad }} - {{ value }} </li>
      </ul>
    </div>

  </div>

  <div>
    <h1>Acciones con js</h1>

    <button @click="soyUnBoton('Boton1')">Dame un click</button>
    <button @click="soyUnBoton('Boton2')">Dame un click</button>
  </div>

</template>

<style>
.index{
  color: white;
}
h1{
  text-align: center;
}
</style>