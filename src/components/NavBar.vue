<template>
    <nav class="navbar">
      <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/9/98/International_Pok%C3%A9mon_logo.svg/1200px-International_Pok%C3%A9mon_logo.svg.png" 
      class="nav-logo">
      <ul class="nav-links">
        <li class="nav-links--item"><a href="#" class="nav-links--link">Home</a></li>
        <li class="nav-links--item"><a href="https://pokeapi.co/" class="nav-links--link">API</a></li>
      </ul>
    </nav>
</template>

<script>
  export default {
    
  }
</script>

<style lang="scss" scoped>
  .navbar {
    display: flex;
    flex-wrap: wrap;
    flex-direction: column;
    top: 0px;
    height: 8em;
    width: 100%;
    align-self: stretch;
    justify-content: center;
    background-color: #f54842
  }
  .nav-logo {
    height: 100px; 
    width: 300px;
    margin-left: 10px;
    align-self: flex-start
  }
  .nav-links {
    display: flex;
    align-self: flex-end;
    justify-self: stretch;
    list-style-type: none;
    margin-right: 20px
  }
  .nav-links--item {
    font-weight: bold;
    font-size: 2em
  }
  .nav-links--link {
    color: white;
    text-decoration: none;
    margin-left: 1em;
  }
</style>