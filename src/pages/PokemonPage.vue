<template>
   <h1>¿Quién es este pokemon?</h1>
   <!--TODO: PICTURE (IMG-->

   <!--TODO: OPCIONES-->
   <PokemonPicture :pokemonId="151" :showPokemon="true"></PokemonPicture>
   <PokemonOptions />
</template>


<script>
import PokemonOptions from '@/components/PokemonOptions.vue'
import PokemonPicture from '@/components/PokemonPicture.vue'
import getPokemonOptions from '@/helpers/getPokemonOptions' 

//console.log(getPokemonOptions());
export default {
        components: {PokemonOptions, PokemonPicture}
    }
</script>

