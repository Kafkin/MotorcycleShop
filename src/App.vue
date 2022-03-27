<template>
  
  <section>

    <video src="./assets/img,icon,video/smoke.mp4" autoplay  muted ref="BgSmokeVideo"></video>
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
