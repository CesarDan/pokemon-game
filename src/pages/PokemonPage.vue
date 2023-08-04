<template>
   <h1>¿QUIÉN ES ÉSTE POKEMON?</h1>
   <!--TODO: PICTURE (IMG-->

   <!--TODO: OPCIONES-->
   <PokemonPicture :pokemonId="151" :showPokemon="true"/>
   <PokemonOptions :pokemons="pokemonArr" />
</template>


<script>
import PokemonOptions from '@/components/PokemonOptions.vue'
import PokemonPicture from '@/components/PokemonPicture.vue'
import getPokemonOptions from '@/helpers/getPokemonOptions' 

//console.log(getPokemonOptions());
export default {
        components: {PokemonOptions, PokemonPicture},
        data() {
            return {
                pokemonArr:[],
                pokemon: null
            }
        },
        methods: {
            async mixPokemonArray() {
                this.pokemonArr = await getPokemonOptions()
                console.log(this.pokemonArr);
            }
        },
        mounted(){
           this.mixPokemonArray()
        }

    }
</script>

