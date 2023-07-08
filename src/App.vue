<template>
  <div class="hero">
    <video autoplay loop muted playsinline="" class="video-pokemon">
      <source src="./assets/videos/pokemon_animado.mp4">
    </video>
    <div class="flex justify-center nav">
      <img alt="Vue logo" src="./assets/img/pokemon.png">
    </div>
    <div class="container mx-auto px-4 sm:flex-col sm:shrink-0">
      <pokemones/>
    </div>
  </div>
</template>

<script>
import Pokemones from "@/components/Pokemones.vue"

export default {
  name: 'App',
  components: {
    'pokemones': Pokemones
  }
}
</script>

<style>
.nav{
  background-color: transparent;
  
}


.video-pokemon{
  width: 100%;
  height: 100vh;
  position: absolute;
  object-fit: cover;
  z-index: -1;
  
}
@media screen and (max-width: 320px){
  .video-pokemon{
    width: 100%;
    height: 100vh;
  }
}
</style>
