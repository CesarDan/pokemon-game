<template>
   <h1>¿Quién es éste pokemon xD?</h1>
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
                pokemonArr:[]
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

