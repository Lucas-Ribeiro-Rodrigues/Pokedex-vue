<template>
  <div class="footer font-white font-big">
      <span class="flex">Criado por Lucas Ribeiro Rodrigues</span>
      <div class="social-media flex">
        <i class="fa fa-twitter icon" aria-hidden="true"/>
        <i class="fa fa-instagram icon" aria-hidden="true"/>
        <i class="fa fa-facebook-official icon" aria-hidden="true"/>
      </div>
      <span class="flex">Coisa na direita</span>
  </div>
</template>

<script>
  export default {
    
  }
</script>

<style lang="scss" scoped>
  .footer {
    display: flex;
    height: 4em;
    bottom: 0px;
    flex-direction: row;
    justify-content: space-around;
    background-color: #f54842;
    align-self: stretch;
    align-items: center;
  }
  .social-media {
    display: flex;
    justify-content: center;
  }
  .icon {
    padding: 0px 10px;
  }
  .font-white {
    font-weight: bold;
    color: white;
  }
  .font-big {
    font-size: 30px;
  }
  .flex {
    flex: 1,
  }
</style>