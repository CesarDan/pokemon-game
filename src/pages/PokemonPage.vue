<template>

   <h1 v-if="!pokemon">Espere por favor...</h1>
    <div v-else>
   <h1>¿QUIÉN ES ÉSTE POKEMON?</h1>
   <PokemonPicture 
        :pokemonId="pokemon.id" 
        :showPokemon="showPokemon"
    />

   <PokemonOptions 
        :pokemons="pokemonArr" 
        @selectionPokemon="checkAnswer"
    />
    

   
    <template v-if="showAnswer">
    <h2 class="fade-in">{{message}}</h2>
    <button @click="newGame">
        Nuevo juego
    </button>
    </template>

</div>
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
                pokemon: null,
                showPokemon: false,
                showAnswer: false,
                message: ''
            }
        },
        methods: {
            async mixPokemonArray() {
                this.pokemonArr = await getPokemonOptions()
                const rndInt = Math.floor(Math.random() * 4)
                this.pokemon = this.pokemonArr[rndInt]
                //console.log(this.pokemonArr);
            },
         checkAnswer(selectedId){
            this.showPokemon = true
            this.showAnswer = true

            if(selectedId == this.pokemon.id){
                this.message = `Correcto, ${this.pokemon.name}`
            }else{
                this.message = `Oops, era ${this.pokemon.name}`
            }
         },

         newGame(){
            this.showPokemon = false
            this.showAnswer = false
            this.pokemonArr = []
            this.pokemon = null,
            this.message = '',
            this.mixPokemonArray()
         }

        },
        mounted(){
           this.mixPokemonArray()
        }

    }
</script>

