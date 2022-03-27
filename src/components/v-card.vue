<template>
  
  <div class="emptyCard" v-if="arrayItem.id === 'none'">
    <div class="emptyCardImg"></div>
  </div>

  <div class="containerCard" v-else v-cloak>
    <img :src="require(`../assets/img,icon,video/${arrayItem.img}`)" :alt="arrayItem.title" @click="$emit('nextMotorcycle', arrayItem)">
    <div class="info">
      <div class="title">
        <h1>Название: </h1>
        <h2>{{ arrayItem.title }}</h2>
      </div>
      <div class="price">
        <h1>Цена: </h1>
        <h2>{{ arrayItem.price }}</h2>
        <h3>{{ arrayItem.currency }}</h3>
      </div>
    </div>
  </div>
  
</template>

<script>
export default {
  data(){
    return{

    }
  },

  methods:{
    
  },

  props:{
    arrayItem: {
      type: Object
    }
  }
}
</script>

<style>
@import url('../assets/styles/Card.css');

</style>