<template>
  <div class="w-full max-w-sm text-center backdrop-contrast-50 bg-tranparent border border-violet-600 rounded-lg shadow-lg shadow-indigo-950 dark:border-purple-950">
    <div class="p-5">
        <a href="#">
            <h4 class="mb-2 text-3xl font-bold tracking-tight text-gray-900 dark:text-white">#{{ pokemon.id }} {{ capitalized(pokemon.name) }}</h4>
        </a>
        
    </div>
    <div class="flex justify-center">
      <img class="rounded-t-lg w-40" :src="pokemon.sprites.front_default" alt="pokemon-image"/>
    </div>
    
    <div class="flex p-5 gap-8 justify-center">
      <div v-for="(tipo,index) in pokemon.tipo" :key="index" 
      class="px-3 py-2 text-md font-medium w-60 text-white hover:bg-red-800"
      :class="typeTraslate(tipo.type.name).color">
        {{ typeTraslate(tipo.type.name).type }}
      </div>
    </div>

    <div class="flex-col justify-center">
      <h2 class="text 4xl font-bold">Experiencia base</h2>
      <h2 class="text-black font-bold">{{ pokemon.experience }}</h2>
    </div>
    
  </div>
</template>

<script>
export default {
  name: 'CardImage',
  props: {
    pokemon:{
      type:Object,
      required:true,
    }
  },
  //data: function(){},
  
  //computed:{},
  methods:{
    typeTraslate(typePokemon){
      const diccionario ={
      'fire':{type: 'Fuego', color:'bg-red-600'},
      'flying':{type:'Volador', color:'bg-sky-300'},
      'normal':{type:'Normal', color:'bg-gray-900'},
      'steel':{type:'Acero', color:'bg-gray-900'},
      'water':{type:'Agua', color:'bg-sky-500'},
      'electric':{type:'Eléctrico', color:'bg-yellow-300'},
      'grass':{type:'Planta', color:'bg-green-500'},
      'ice':{type:'Hielo', color:'bg-sky-500'},
      'fighting':{type:'Lucha', color:'bg-red-800'},
      'poison':{type:'Veneno', color:'bg-violet-600'},
      'ground':{type:'Tierra', color:'bg-yellow-950'},
      'psychic':{type:'Psíquico', color:'bg-purple-800'},
      'bug':{type:'Bicho', color:'bg-green-500'},
      'rock':{type:'Roca', color:'bg-stone-600'},
      'ghost':{type:'Fantasma', color:'bg-indigo-950'},
      'dragon':{type:'Dragón', color:'bg-rose-500'},
      'dark':{type:'Siniestro', color:'bg-fuchsia-950'},
      'fairy':{type:'Hada', color:'bg-fuchsia-400'}
      }
      return diccionario[typePokemon]
    },
    capitalized(name) {
      const capitalizedFirst = name[0].toUpperCase();
      const rest = name.slice(1);

      return capitalizedFirst + rest;
    },
  }
  //   for(item of lista){
  //     item_es=diccionario[item]
  //     traducido = espanol.push(item_es)
  //   }
  //   return espanol
  //     }
  // },
  //-- Lifecycle Methods
}

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
