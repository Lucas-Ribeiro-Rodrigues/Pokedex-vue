<template>
  <div id="app">
    <NavBar />
    <PokemonsList/>
    <Footer />
  </div>
</template>

<script>
import PokemonsList from './components/PokemonsList.vue'
import NavBar from './components/NavBar'
import Footer from './components/Footer'

export default {
  name: 'App',
  components: {
    PokemonsList,
    NavBar,
    Footer
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  display: flex;
  flex-direction: column;
  align-items: center;
  height: 100%;
  width: 100%;
  background-color: #abe1eb
}
</style>
