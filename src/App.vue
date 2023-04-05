<script setup>
import Chat from './components/Chat.vue';
import Pasobebe from './components/Pasobebe.vue';
import ReactiviadEjemplo from './components/ReactividadEjemplo.vue';
import CrudVue from './components/CrudVue.vue';
import ApiAnime from './components/ApiAnime.vue';
</script>

<template>

  <main class="space">
    <Pasobebe></Pasobebe>
    <br>
    <ReactiviadEjemplo></ReactiviadEjemplo>
    <br>
    <CrudVue></CrudVue>
    <br>
    <ApiAnime></ApiAnime>
  </main>
  
</template>

<style>
.space{
  width: 100%;
}
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