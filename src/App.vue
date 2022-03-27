<template>
  
  <section>
    <div class="container">
      <ul class="navBar">
        <li class="logo">
          <img src="./assets/img,icon,video/logoWheel.png" alt="">
          <h1>Biker Wheel</h1>
        </li>
        <li class="navigation">
          <h1 v-for="(item, index) in pages" :class="{ 'active':currnetPages === index }" :key="index" @click="currnetPages = index">{{ item.title }}</h1>
        </li>
      </ul>

      <div id="loader" v-if="isLoading === true">
        <div l a></div>
        <div l b></div>
        <div l c></div>
        <div l d></div>
        <div l e></div>
        <div l f></div>
        <div l g></div>
        <div l h></div>
      </div>

      <div class="carousel" v-else-if="isLoading === false && currnetPages === 2" v-cloak>
        <vCard v-for="(item, index) in arrayMotocycle" :key="index" :arrayItem="item" @nextMotorcycle="nextMotorcycle" @buy="buy" :class="{ 'front': index === (maxIndex - 1) }" v-show="maxIndex >= index && minIndex <= index"></vCard>
      </div>

      <div class="ShoppingCart" v-if="currnetPages === 0">
        <ul>
          <li v-for="(item, index) in ShoppingCartArray" :key="index">
            <img :src="require(`./assets/img,icon,video/${item.img}`)" alt="">
            <div class="info-buy-card">
              <h1>Название: </h1>
              <h2>{{ item.title }}</h2>
            </div>
            <div class="info-buy-card">
              <h1>Цена: </h1>
              <h2>{{ item.price }}</h2>
              <h3>{{ item.currency }}</h3>
            </div>
            <div class="info-buy-card">
              <h1>Колличество: </h1>
              <h2>{{ item.countNow }}</h2>
            </div>
            <div class="info-buy-card">
              <h1>Общая цена: </h1>
              <h2>{{ item.price * item.countNow }}</h2>
              <h3>{{ item.currency }}</h3>
            </div>
          </li>
        </ul>
      </div>

      <ul class="pairs">
        <li>
          <img src="./assets/img,icon,video/pairsOne.png" alt="">
          <img src="./assets/img,icon,video/pairsTwo.png" alt="">
          <img src="./assets/img,icon,video/pairsThree.png" alt="">
        </li>
      </ul>
    </div>
    
    <video src="./assets/img,icon,video/smoke.mp4" autoplay loop muted ref="BgSmokeVideo"></video>
  </section>

</template>

<script>
import vCard from './components/v-card.vue'

export default {
  name: 'App',
  data(){
    return{
      pages: [],
      currnetPages: 2,
      currentCard: null,
      arrayMotocycle: [],
      arrayEmpty: true,
      isLoading: true,
      countShowCard: 3,
      maxIndex: 2,
      minIndex: 0,
      maxStandart: 2,
      minStandart: 0,
      ShoppingCartArray: []
    }
  },

  watch:{
    currentCard(val){
      if(this.ShoppingCartArray.includes(val)){
        return
      }else{
        this.ShoppingCartArray.push(val)
        console.log('Массив: ', this.ShoppingCartArray);
      }
    }
  },

  methods:{
    nextMotorcycle(card){
      let index = this.arrayMotocycle.indexOf(card)
      console.log( index );

      this.maxIndex = index + 1
      this.minIndex = index - 1
    },

    buy(cardInfo){
      console.log('Середина была: ', this.currentCard);
      this.currentCard = cardInfo
      console.log('Середина стала: ', this.currentCard);
    }
  },
  
  components: {
    vCard,
  },

  computed(){
    this.$refs.BgSmokeVideo.playbackRate = 1
  },

  mounted(){
    const getData = async (url) => {
      const response = await fetch(url)
      const data = response.json()
      return data
    }

    getData('http://localhost:3000/Motorcycle').then((data) => {
      this.arrayMotocycle = data
      this.isLoading = false
      console.log(this.arrayMotocycle);
    })

    getData('http://localhost:3000/Pages').then((data) => {
      this.pages = data
      console.log(this.pages);
    })
  }
}
</script>

<style>
@import url('./assets/styles/App.css');

</style>
