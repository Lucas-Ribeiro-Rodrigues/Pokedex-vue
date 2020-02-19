<template>
  <div class="poke-row">
    <div v-for="(evolution, index) in this.evolutions" v-bind:key="index">
      <PokemonCard :image="evolution.image"
      :name="evolution.name" v-bind:types="evolution.types"/>
    </div>
  </div>
</template>

<script>
  import PokemonCard from './PokemonCard'
  const axios = require('axios')

  export default {
    data() {
      return {
        pokemons: [],
        evolutions: [
        {
          name: "bulbasaur",
          image: "https://vignette.wikia.nocookie.net/pokedex/images/2/24/Bubassaur.png/revision/latest/scale-to-width-down/340?cb=20141012190624&path-prefix=pt-br",
          types: ['grass', 'poison']
        },
        {
          name: "ivysaur",
          image: "https://cdn.bulbagarden.net/upload/thumb/7/73/002Ivysaur.png/250px-002Ivysaur.png",
          types: ['grass', 'poison']
        },
        {
          name: "venosaur",
          image: "https://assets.pokemon.com/assets/cms2/img/pokedex/full/003.png",
          types: ['grass', 'poison']
        }
        ]
      } 
    },
    components: {
      PokemonCard
    },
    methods: {
      getPokemons() {
        return axios.get('https://pokeapi.co/api/v2/pokemon/?limit=151')
          .then(result => result.data.results)
      },
      findPokemon() {
        
      }
    },
    async beforeMount() {
      this.pokemons = await this.getPokemons()
      this.evolutions = await this.findPokemon(this.pokemons[0])
    }
  }
</script>

<style lang="scss" scoped>
  .poke-row {
    display: flex;
    flex-grow: 1;
    flex-direction: row;
    justify-content: space-around;
    align-self: stretch;
    align-items: center;
  }
</style>