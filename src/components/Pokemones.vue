<template>
    <div>
        <buscador @buscarPokemon="setNamePokemon"/>
        <div class="container flex sm:columns-auto justify-center gap-9 mt-16 " v-if="pokemonName !== ''">
            <card-image :pokemon="pokemonInfo"/>
            <card-habilidad :pokemon="pokemonInfo"/>
        </div>
    </div>
</template>

<script>

import Buscador from "@/components/Buscador.vue"
import CardImage from "./CardImage.vue";
import CardHabilidades from './CardHabilidades.vue';
export default {
    name: 'pokemon-comp',
    // props: {},
    data: function(){
        return {
            pokemonName:'',
            pokemonInfo: {
                id:'',
                name:'',
                sprites: '',
                tipo: '',
                stats: [],
                experience:''
            },
        }
    },
    // computed: {},
    methods: {
        setNamePokemon(name){
            this.pokemonName = name;
        },
        async getPokemon(){
            try{
                let response = await fetch(`https://pokeapi.co/api/v2/pokemon/${this.pokemonName}`);
                let data = await response.json();
                this.pokemonInfo.id = data.id;
                this.pokemonInfo.name = data.name;
                this.pokemonInfo.sprites = data.sprites;
                this.pokemonInfo.tipo = data.types;
                this.pokemonInfo.stats = data.stats
                this.pokemonInfo.experience = data.base_experience
                console.log(data.base_experience)
            }
            catch(error){
                console.log(error);
            }
        }
    },
    watch: {
        pokemonName(value){
            if(value != ''){
                this.getPokemon()
            }
        }
    },
    components: {
        'buscador': Buscador,
        'card-image': CardImage,
        'card-habilidad': CardHabilidades
    },
    // mixins: [],
    // filters: {},
    // -- Lifecycle Methods

    // -- End Lifecycle Methods
}
</script>

<style scoped>
    
</style>