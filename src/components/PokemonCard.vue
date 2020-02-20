<template>
  <div class="card poke-card" >
    <img :src=this.image alt="Pokemon" class="card-image">
    <div>
      <h3 style="margin: 10px">{{capitalize(this.name)}}</h3>
      <div class="card-text">
        <ul class="types-list">
          <li v-for="(type, index) in types" v-bind:key="index">
              <i :class="type.icon.class" :style="type.icon.style"/>
              {{type.type.name}}
          </li>
        </ul>
      </div>
    </div>
  </div>
</template>

<script>
  export default {
    data() {
      return {
        iconTypes: {
          "poison" : {
            class: "fas fa-skull-crossbones fa-1x",
            style: "color: purple"
          },
          "grass" : {
            class: "fas fa-leaf fa-1x",
            style: "color: green"
          },
          "dragon": {
            class: "fas fa-dragon fa-1x",
            style: "color: orange"
          },
          "ground": {
            class: "fas fa-mountain fa-1x",
            style: "color: brown"
          },
          "bug" : {
            class: "fas fa-bug fa-1x",
            style: "color: #00a621"
          },
          "fire": {
            class: "fas fa-fire fa-1x",
            style: "color: #fc6f03" 
          },
          "ice": {
            class: "fas fa-icicles fa-1x",
            style: "color: #aef2f5"
          },
          "normal": {
            class: "fas fa-star-of-life fa-1x",
            style: "color: #737373"
          },
          "water": {
            class: "fas fa-tint fa-1x",
            style: "color: #07d3e6"
          },
          "electric": {
            class: "fas fa-bolt fa-1x",
            style: "color: yellow"
          },
          "fighting": {
            class: "fas fa-hand-rock fa-1x",
            style: "color: #eec1ad"
          },
          "flying": {
            class: "fas fa-dove fa-1x",
            style: "color: white"
          },
          "psychic": {
            class: "far fa-eye fa-1x",
            style: "color: violet"
          },
          "rock": {
            class: "fas fa-gem fa-1x",
            style: "color: grey"
          },
          "ghost": {
            class: "fas fa-ghost fa-1x",
            style: "color: white"
          },
        }
      }
    },
    props: {
      image: Image,
      name: String,
      types: Array[String],
    },
    methods: {
      loadTypesIcons() {
        this.types.map(elem => {
          elem.icon = this.iconTypes[elem.type.name]
          return elem
        })
      },
      capitalize(string) {
        return string.charAt(0).toUpperCase() + string.slice(1)
      }
    },
    watch: {
      types: {
        immediate: true,
        handler() {
          this.loadTypesIcons()
        }
      }
    },
  }
</script>

<style lang="scss" scoped>
  .poke-card {
    display: flex;
    flex-direction: column;
    border: none
  }
  .card-image {
    min-width: 150px;
    min-height: 150px;
    max-width: 400px;
    max-height: 400px;
  }
  .card-text {
    display: flex;
    flex-direction: row;
    justify-content: center
  }
  .types-list {
    display: flex;
    flex-direction: column;
    margin: 0;
    padding-left: 4px;
    list-style-type: none;
  }
</style>