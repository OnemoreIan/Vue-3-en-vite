<script setup>
import Chat from './components/Chat.vue';
import Pasobebe from './components/Pasobebe.vue';
import ReactiviadEjemplo from './components/ReactividadEjemplo.vue';
import CrudVue from './components/CrudVue.vue';
import ApiAnime from './components/ApiAnime.vue';

</script>

<template>
  <Pasobebe></Pasobebe>
  <br>
  <ReactiviadEjemplo></ReactiviadEjemplo>
  <hr>
  <CrudVue></CrudVue>
  <br>
  <ApiAnime></ApiAnime>

</template>

<style>
.index{
  color: white;
}
h1{
  text-align: center;
}
.rojo{
  background-color: black;
  color: white;
}
</style>