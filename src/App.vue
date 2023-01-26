<script setup>
  import PokedexVue from './components/PokedexView.vue';
</script>

<template>
  <link href="https://fonts.cdnfonts.com/css/pokemon-solid" rel="stylesheet">
  <div id="app">
    <Suspense>
      <PokedexVue />
    </Suspense>
  </div>
</template>

<style>
  @import url('https://fonts.cdnfonts.com/css/pokemon-solid');
  html {
    background-color: #212121;
    font-family: 'Pokemon Solid', sans-serif;
    font-size: 1.5rem;
  }

  .text-center {
  text-align: center;
  color: #fdcc01;
  -webkit-text-stroke: 0.55px #3a58a3;
  }
</style>