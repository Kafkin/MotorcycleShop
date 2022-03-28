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
      <div class="buy">
        <input type="range" min="0" :max="arrayItem.countStock" v-model="count">
        <div class="count">
          <h2>{{ count }}</h2>
        </div>
        <button class="btnBuy" @click="Buy(arrayItem, count)">Купить</button>
      </div>
    </div>
  </div>
  
</template>

<script>
export default {
  data(){
    return{
      count: 1
    }
  },

  methods:{
    Buy(arrayItem, count){
      console.log('Начало: ', arrayItem, count)
      arrayItem.countNow = count
      fetch('http://localhost:3000/store', {
        method: 'POST',
        // body: JSON.stringify(data),
        headers: {
          'Accept': 'application/json',
          'Content-Type': 'application/json'
        },
        body: JSON.stringify(arrayItem),
      })
      // this.$emit('buy', arrayItem)
    }
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