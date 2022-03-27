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

      <div class="carousel">
        <img src="./assets/img,icon,video/MotorcycleOne.png" alt="">
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
export default {
  name: 'App',
  data(){
    return{
      
    }
  },

  methods:{

  },
  
  components: {

  },

  computed(){
    this.$refs.BgSmokeVideo.playbackRate = 1
  }
}
</script>

<style>
@import url('./assets/styles/App.css');

</style>
