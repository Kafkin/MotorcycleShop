<template>
  
  <section>
    <div class="container">
      <ul class="navBar">
        <li class="logo">
          <img src="./assets/img,icon,video/logoWheel.png" alt="">
          <h1>Biker Wheel</h1>
        </li>
        <li class="navigation">
          <h1 class="active">Shopping cart</h1>
          <h1>Gallery</h1>
          <h1>Store</h1>
          <h1>Contact</h1>
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

      <div class="carousel" v-else v-cloak>
        <vCard v-for="(item, index) in arrayMotocycle" :key="index" :arrayItem="item" @nextMotorcycle="nextMotorcycle" :class="{ 'front': index === (maxIndex - 1) }" v-show="maxIndex >= index && minIndex <= index"></vCard>
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
      arrayMotocycle: [],
      arrayEmpty: true,
      isLoading: true,
      countShowCard: 3,
      maxIndex: 2,
      minIndex: 0,
      maxStandart: 2,
      minStandart: 0
    }
  },

  methods:{
    nextMotorcycle(card){
      let index = this.arrayMotocycle.indexOf(card)
      console.log( index );

      this.maxIndex = index + 1
      this.minIndex = index - 1
      // this.maxIndex = this.maxStandart + (index * this.countShowCard)
      // this.minIndex = this.minStandart + (index * this.countShowCard)
    }
  },
  
  components: {
    vCard
  },

  computed(){
    this.$refs.BgSmokeVideo.playbackRate = 1
  },

  mounted(){
    fetch('http://localhost:3000/Motorcycle')
      .then(json => json.json())
      .then(data => {
        this.arrayMotocycle = data
        this.isLoading = false
      })
  }
}
</script>

<style>
@import url('./assets/styles/App.css');

</style>
