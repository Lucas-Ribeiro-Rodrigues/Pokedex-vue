<template>
  <div class="poke-row" v-on:keydown.right="slideForward" v-on:keydown.left="slideBack">
  <a href="#" v-on:click.prevent="slideBack" style="color:#2c3e50; margin-left: 5vw">
    <i class="fas fa-arrow-left fa-3x" aria-hidden="true"/>
  </a>
    <div v-for="(evolution, index) in this.evolutions" v-bind:key="index">
      <PokemonCard :image="evolution.image"
      :name="evolution.name" v-bind:types="evolution.types"/>
    </div>
  <a href="#" v-on:click="slideForward()" style="color:#2c3e50; margin-right: 5vw">
    <i class="fas fa-arrow-right fa-3x" aria-hidden="true"/>
  </a>
  </div>
</template>

<script>
  import PokemonCard from './PokemonCard'
  const axios = require('axios')

  export default {
    data() {
      return {
        pokemons: [],
        evolutions: [],
        prevEvolutionStack: [],
        nextEvolutionStack: [],
        prevNumberOfEvolutions: 0
      } 
    },
    components: {
      PokemonCard
    },
    methods: {
      getPokemons() {
        return axios.get('https://pokeapi.co/api/v2/pokemon/?limit=151')
          .then(response => response.data.results)
      },
      formatPokemon(pokemon) {
        return {
          id: pokemon.id,
          name: pokemon.name,
          types: pokemon.types,
          image: pokemon.sprites.front_default
        }
      },
      async findPokemon(pokemon) {
        return axios.get(pokemon.url)
          .then(response => this.formatPokemon(response.data))
      },
      async findEvolutions(pokemon) {
        const numberOfEvolutions = await this.findNumberOfEvolutions(pokemon)
        let evolutions = [pokemon]
        for(let i=pokemon.id+1; i<=pokemon.id + numberOfEvolutions; i++)
        {
          const pokemon = await axios.get(`https://pokeapi.co/api/v2/pokemon/${i}`)
                                .then(response => response.data)
          evolutions.push(this.formatPokemon(pokemon))
        }
        return evolutions
      },
      async findNumberOfEvolutions(pokemon) {
        let evolutionChain = await axios.get(`https://pokeapi.co/api/v2/evolution-chain/${Math.ceil(pokemon.id/3)}`)
                                .then(response => response.data.chain.evolves_to[0])
        let numberOfEvolutions = 0
        while(evolutionChain)
        {
          numberOfEvolutions++
          evolutionChain = evolutionChain.evolves_to[0]
        }
        return numberOfEvolutions
      },
      async slideBack() {
        if(this.evolutions[0].id == 1)
          return;

        this.nextEvolutionStack.push(this.evolutions)
        this.evolutions = this.prevEvolutionStack.pop()
      },
      async slideForward() {
        if(this.evolutions[this.evolutions.length-1].id == 151)
          return;
        

        if(this.nextEvolutionStack.length == 0 && this.evolutions[this.evolutions.length-1].id != 151) {
          const pokemon = await this.findPokemon(this.pokemons[this.evolutions[this.evolutions.length-1].id])
          const evolutions = await this.findEvolutions(pokemon)
          this.nextEvolutionStack.push(evolutions)
        
        }
        this.prevEvolutionStack.push(this.evolutions)
        this.evolutions = this.nextEvolutionStack.pop()
      }
    },
    async beforeMount() {
      this.pokemons = await this.getPokemons()
      const pokemon = await this.findPokemon(this.pokemons[0])
      this.evolutions = await this.findEvolutions(pokemon)
    },
    computed: {
      
    }
  }
</script>

<style lang="scss" scoped>
  .poke-row {
    display: flex;
    flex-grow: 1;
    flex-direction: row;
    justify-content: space-between;
    align-self: stretch;
    align-items: center;
  }
  a {
    position: relative;
  }
</style>