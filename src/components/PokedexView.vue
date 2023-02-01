<script setup> 
  import {ref, computed} from 'vue';
  import PokemonVue from './PokemonView.vue';

  const response = await fetch('https://pokeapi.co/api/v2/pokemon?limit=151'),
        pokemons = ref(await response.json());
  
  var search = ref('');

  var filteredPokemons = computed(() => Object.values(pokemons.value.results).filter(pkmn => pkmn.name.toLowerCase().includes(search.value.toLowerCase())));
</script>

<template>
  <div class="top">
    <img src="/src/assets/icons/search.png" alt="">
    <h1 class="text-center">VueDex</h1>
    <input type="text" v-model="search" placeholder="Buscar Pokémon">
  </div>
  <div class="container">
    <Suspense v-for="pkmn in filteredPokemons" :key="pkmn">
      <PokemonVue :pokemon="pkmn"/>
    </Suspense>
  </div>
</template>

<style>
.container {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
  gap: 1rem;
  margin: 0% 10%;
}
.top {
  background-color: rgb(89, 86, 82);
  display: flex;
  flex-direction: column;
  align-items: center;
  margin-bottom: 5%;
  padding-bottom: 2%;
}
/* make the input pokemon style */
input {
  border: 1px solid #fdcc01;
  border-radius: 35px;
  background-color: #af9a9a;
  color: #fdcc01;
  -webkit-text-stroke: 0.55px #3a58a3;
  font-family: 'Pokemon Solid', sans-serif;
  font-size: 1.5rem;
  text-align: center;
}
h1 {
  margin: 0%;
}
</style>