<template>
  <div id="app">
    <div class="container">
    <spotifyHeader :SentGenreArray="genreArray" @ChangedGenre="SendSelectedGenre"/>
    <spotifyMain :SentSelectedGenre="SelectedGenre" @ObtainGenres="SendGenres"/>
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
  },

  data(){
    return{
      genreArray:[],
      SelectedGenre:""
    }
  },

  methods:{
    SendGenres(genreArray){
    this.genreArray=genreArray;
    },
    SendSelectedGenre(SelectedGenre){
    this.SelectedGenre=SelectedGenre;
    }
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
