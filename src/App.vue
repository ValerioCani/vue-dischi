<template>
  <div id="app">
    <div class="container">
    <spotifyHeader :SentGenreArray="genreArray" :SentArtistArray="artistArray" @ChangedGenre="SendSelectedGenre" @ChangedArtist="SendSelectedArtist"/>
    <spotifyMain :SentSelectedGenre="SelectedGenre" :SentSelectedArtist="SelectedArtist" @ObtainGenres="SendGenres" @ObtainArtist="SendArtist"/>
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
      artistArray:[],
      SelectedGenre:"",
      SelectedArtist:""
    }
  },

  methods:{
    SendGenres(genreArray){
    this.genreArray=genreArray;
    },
    SendArtist(artistArray){
    this.artistArray=artistArray;
    },
    SendSelectedGenre(SelectedGenre){
    this.SelectedGenre=SelectedGenre;
    },
    SendSelectedArtist(SelectedArtist){
    this.SelectedArtist=SelectedArtist;
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
