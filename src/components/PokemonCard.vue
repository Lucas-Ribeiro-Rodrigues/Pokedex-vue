<template>
  <div class="card poke-card" >
    <img :src=this.image alt="Pokemon" class="card-image">
    <div>
      <h3>{{this.name}}</h3>
      <div class="card-text">
        Tipos: 
        <ul class="types-list">
          <li v-for="(type, index) in types" v-bind:key="index">{{type}}, 
          </li>
        </ul>
      </div>
    </div>
  </div>
</template>

<script>
  export default {
    props: {
      image: Image,
      name: String,
      types: Array[String],
    }
  }
</script>

<style lang="scss" scoped>
  .poke-card {
    display: flex;
    flex-direction: column;
    border: none
  }
  .card-image {
    max-width: 200px;
    max-height: 200px;
  }
  .card-text {
    display: flex;
    flex-direction: row;
    justify-content: center
  }
  .types-list {
    display: flex;
    margin: 0;
    padding-left: 4px;
    list-style-type: none;
  }
</style>