<template>
    
    <div class="w-full max-w-sm p-4 backdrop-contrast-50 opacity-120 bg-tranparent border border-gray-400 rounded-lg shadow-lg shadow-emerald-700 sm:p-6 dark:bg-gray-800 dark:border-gray-700">
        <h5 class="mb-3 text-base font-bold text-gray-900 md:text-xl dark:text-white">
            Habilidades
        </h5>
        <ul class="my-4 space-y-3" v-if="puntosCombate.hp">
            <li>
                <div class="flex mb-1 gap-1">
                    <img width="20" height="20" src="https://img.icons8.com/emoji/48/heart-suit.png" alt="heart-suit"/>
                    <span class="text-base font-bold text-blue-700 dark:text-white">Salud</span>
                </div>
                <div class="w-full bg-gray-200 rounded-full h-2.5 dark:bg-gray-700">
                    <div 
                    class="bg-blue-600 text-xs font-medium text-blue-100 text-center p-0.5 leading-none rounded-full" 
                    :style="{width: puntosCombate.hp/2+'%'}"
                    :class="colorChange(puntosCombate.hp)"> {{ puntosCombate.hp }}</div>
                </div>
            </li>
            <li>
                <div class="flex mb-1 gap-1">
                    <img width="20" height="20" src="https://img.icons8.com/external-soft-fill-juicy-fish/60/external-component-game-development-soft-fill-soft-fill-juicy-fish-9.png" alt="external-component-game-development-soft-fill-soft-fill-juicy-fish-9"/>
                    <span class="text-base font-bold text-blue-600 dark:text-white">Ataque</span>
                </div>
                <div class="w-full bg-gray-200 rounded-full h-2.5 dark:bg-gray-700">
                    <div 
                    class="bg-blue-600 text-xs font-medium text-blue-100 text-center p-0.5 leading-none rounded-full" 
                    :style="{width: puntosCombate.attack/2+'%'}"
                    :class="colorChange(puntosCombate.attack)"> {{ puntosCombate.attack }}</div>
                </div>
            </li>
            <li>
                <div class="flex mb-1 gap-1">
                    <img width="25" height="25" src="https://img.icons8.com/color/48/knight-shield.png" alt="knight-shield"/>
                    <span class="text-base font-bold text-blue-600 dark:text-white">Defensa</span>
                </div>
                <div class="w-full bg-gray-200 rounded-full h-2.5 dark:bg-gray-700">
                    <div 
                    class="bg-blue-600 text-xs font-medium text-blue-100 text-center p-0.5 leading-none rounded-full" 
                    :style="{width: puntosCombate.defens/2+'%'}"
                    :class="colorChange(puntosCombate.defens)"> {{ puntosCombate.defens }}</div>
                </div>
            </li>
            <li>
                <div class="flex mb-1 gap-1">
                    <img width="20" height="20" src="https://img.icons8.com/color/48/fist-pokemon.png" alt="fist-pokemon"/>
                    <span class="text-base font-bold text-blue-600 dark:text-white">Ataque Especial</span>
                </div>
                <div class="w-full bg-gray-200 rounded-full h-2.5 dark:bg-gray-700">
                    <div 
                    class="bg-blue-600 text-xs font-medium text-blue-100 text-center p-0.5 leading-none rounded-full" 
                    :style="{width: puntosCombate.attack_esp/2+'%'}"
                    :class="colorChange(puntosCombate.attack_esp)"> {{ puntosCombate.attack_esp }}</div>
                </div>
            </li>
            <li>
                <div class="flex mb-1 gap-1">
                    <img width="25" height="25" src="https://img.icons8.com/color/48/yellow-team.png" alt="yellow-team"/>
                    <span class="text-base font-bold text-blue-600 dark:text-white">Defensa Especial</span>
                </div>
                <div class="w-full bg-gray-200 rounded-full h-2.5 dark:bg-gray-700">
                    <div 
                    class="bg-blue-600 text-xs font-medium text-blue-100 text-center p-0.5 leading-none rounded-full" 
                    :style="{width: puntosCombate.defens_esp/2+'%'}"
                    :class="colorChange(puntosCombate.defens_esp)"> {{ puntosCombate.defens_esp }}</div>
                </div>
            </li>
            <li>
                <div class="flex mb-1 gap-1">
                    <img width="25" height="25" src="https://img.icons8.com/color/48/instinct.png" alt="instinct"/>
                    <span class="text-base font-bold text-blue-600 dark:text-white">Velocidad</span>
                </div>
                <div class="w-full bg-gray-200 rounded-full h-2.5 dark:bg-gray-700">
                    <div 
                    class="bg-blue-600 text-xs font-medium text-blue-100 text-center p-0.5 leading-none rounded-full" 
                    :style="{width: puntosCombate.speed/2+'%'}"
                    :class="colorChange(puntosCombate.speed)"> {{ puntosCombate.speed }}</div>
                </div>
            </li>
        </ul>
    </div>

</template>

<script>
export default {
    name: 'component-name',
    props: {
        pokemon:{
            type:Object,
            required:true,
        }
    },
    data: function(){
        return {
        }
    },
    computed: { 
        puntosCombate(){
            
            if(this.pokemon.stats.length > 0){
                let puntos ={
                hp: this.pokemon.stats[0].base_stat,
                attack: this.pokemon.stats[1].base_stat,
                defens: this.pokemon.stats[2].base_stat,
                attack_esp: this.pokemon.stats[3].base_stat,
                defens_esp: this.pokemon.stats[4].base_stat,
                speed: this.pokemon.stats[5].base_stat
            }
            return puntos
            }
            return {}
            
        },
    },
    methods: {
        colorChange(porcentaje){
            if(porcentaje <= 40){
                return 'bg-red-600'
                
            };
            if (porcentaje >40 && porcentaje <80){
                return 'bg-yellow-300'
            }
            if(porcentaje >=80){
                return 'bg-green-400'
            }
        }
    }
    // watch: {},
    // components: {},
    // mixins: [],
    // filters: {},
    // -- Lifecycle Methods
    // -- End Lifecycle Methods
}
</script>

<style scoped>
    
</style>