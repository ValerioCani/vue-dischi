<template>
  <div id="app">
    <div class="container">
    <spotifyHeader/>
    <spotifyMain/>
    </div>
  </div>
</template>

<script>
import spotifyHeader from './components/spotifyHeader.vue'
import spotifyMain from './components/spotifyMain.vue'

export default {
  name: 'App',
  components: {
  spotifyHeader,
  spotifyMain
  }
}
</script>

<style lang="scss">
@import'./stylesheets/var.scss';
@import'./stylesheets/general.scss';
#app {
font-family:  monospace;
background-color: $background_color;
height: 100vh;
display: flex;
justify-content: center;
align-items: center;
  .container{
    width: 1440px;
  }
}
</style>
