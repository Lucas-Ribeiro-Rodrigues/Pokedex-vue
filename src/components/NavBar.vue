<template>
    <nav class="navbar">
      <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/9/98/International_Pok%C3%A9mon_logo.svg/1200px-International_Pok%C3%A9mon_logo.svg.png" 
      class="nav-logo">
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
    align-self: center
  }
</style>