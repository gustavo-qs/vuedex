<script setup> 
  const props = defineProps({
    pokemon: Object,
    img: String
  });

  const res = await fetch(props.pokemon.url);
  const pokedata = await res.json();

  const generateGradientClasses = (type1, type2) => {
    return `background: linear-gradient(to bottom, ${getColorFromType(type1)}, ${getColorFromType(type2)});`;
  }

  const getColorFromType = (type1) => {
    switch (type1) {
      case 'bug':
        return '#92BC2C';
      case 'dark':
        return '#595761';
      case 'dragon':
        return '#0C69C8';
      case 'electric':
        return '#F2D94E';
      case 'fire':
        return '#FBA54C';
      case 'fairy':
        return '#EE90E6';
      case 'fighting':
        return '#D3425F';
      case 'flying':
        return '#A1BBEC';
      case 'ghost':
        return '#5F6DBC';
      case 'grass':
        return '#5FBD58';
      case 'ground':
        return '#DA7C4D';
      case 'ice':
        return '#75D0C1';
      case 'normal':
        return '#A0A29F';
      case 'poison':
        return '#B763CF';
      case 'psychic':
        return '#FA8581';
      case 'rock':
        return '#C9BB8A';
      case 'steel':
        return '#5695A3';
      case 'water':
        return '#539DDF';
      default:
        return '#aea9bf';
    }
  };
</script>

<template>
  <div :class="`card ${pokedata.types[0]?.type.name}-gradient ${pokedata.types[1]?.type.name}-gradient`" :style="generateGradientClasses(pokedata.types[0]?.type.name, pokedata.types[1]?.type.name)">
    <p class="zoom text-center">{{ pokemon.name.charAt(0).toUpperCase() + pokemon.name.slice(1) }}</p>
    <img class="zoom" :src="`/src/assets/imgs/${pokedata.id <= 9 ? `00${pokedata.id}` : pokedata.id <= 99 ? `0${pokedata.id}` : `${pokedata.id}`}.png`"><br>
    <div class="icons">
      <img v-if="pokedata.types[0]?.type.name" :class="`icon ${pokedata.types[0]?.type.name}`" :src="`/src/assets/icons/${pokedata.types[0].type.name}.svg`">
      <img v-if="pokedata.types[1]?.type.name" :class="`icon ${pokedata.types[1]?.type.name}`" :src="`/src/assets/icons/${pokedata.types[1].type.name}.svg`">
    </div>
  </div>
</template>

<style>

.card {
  display: flex;
  flex-direction: column;
  align-items: center;
  border: 1px solid white;
  border-radius: 15px;
  width: 100%;
}

.card:hover {
  border: #fdcc01 2px solid;
}

.icon {
  border-radius: 100%;
  height: 2rem;
  width: 2rem;
  transition: 200ms all;
  margin-left: 5%;
}

.icons {
  display: flex;
  justify-content: center;
  margin-bottom: 15%;
}

.icon:hover{
  filter: saturate(700%);
  transform: scale(1.2);
  cursor: pointer;
}

.zoom {
  transition: transform .1s;
  cursor: pointer;
}

.zoom:hover {
  transform: scale(1.2);
}

.bug {
  background: #92BC2C;
  box-shadow: 0 0 20px #92BC2C;
}

.dark {
  background: #595761;
  box-shadow: 0 0 20px #595761;
}

.dragon {
  background: #0C69C8;
  box-shadow: 0 0 20px #0C69C8;
}

.electric {
  background: #F2D94E;
  box-shadow: 0 0 20px #F2D94E;
}

.fire {
  background: #FBA54C;
  box-shadow: 0 0 20px #FBA54C;
}

.fairy {
  background: #EE90E6;
  box-shadow: 0 0 20px #EE90E6;
}

.fighting {
  background: #D3425F;
  box-shadow: 0 0 20px #D3425F;
}

.flying {
  background: #A1BBEC;
  box-shadow: 0 0 20px #A1BBEC;
}

.ghost {
  background: #5F6DBC;
  box-shadow: 0 0 20px #5F6DBC;
}

.grass {
  background: #5FBD58;
  box-shadow: 0 0 20px #5FBD58;
}

.ground {
  background: #DA7C4D;
  box-shadow: 0 0 20px #DA7C4D;
}

.ice {
  background: #75D0C1;
  box-shadow: 0 0 20px #75D0C1;
}

.normal {
  background: #A0A29F;
  box-shadow: 0 0 20px #A0A29F;
}

.poison {
  background: #B763CF;
  box-shadow: 0 0 20px #B763CF;
}

.psychic {
  background: #FA8581;
  box-shadow: 0 0 20px #FA8581;
}

.rock {
  background: #C9BB8A;
  box-shadow: 0 0 20px #C9BB8A;
}

.steel {
  background: #5695A3;
  box-shadow: 0 0 20px #5695A3;
}

.water {
  background: #539DDF;
  box-shadow: 0 0 20px #539DDF;
}

</style>