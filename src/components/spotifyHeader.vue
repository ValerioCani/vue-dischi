<template>
  <header>
    <img src="../assets/logo-small.svg" alt="">
    <div>
      <label for="genre-selector">Select the Genre</label>
      <select name="genre" id="genreSelector" v-model="selected" @change="$emit('ChangedGenre', selected)">
        <option value="">All seleced</option>
        <option v-for="(AlbumGenre, index) in SentGenreArray" :key="index" :value="AlbumGenre">{{AlbumGenre}}</option>
      </select>
    </div>
  </header>
</template>

<script>
export default {
    name:'spotifyHeader',
    props:{
      SentGenreArray:Array
    },
    data(){
      return{
      selected:""
      }
    },
    mounted(){
      console.log(this.selected)
    }
}
</script>

<style scoped lang="scss">
@import'../stylesheets/var.scss';
@import'../stylesheets/general.scss';
header{
height: 55px;
background-color: $primary_color;
display: flex;
justify-content: space-between;
align-items: center;
  img{
  height: 100%;
  padding: 12px;
  }
  div{
  margin-right: 12px;
    label{
    color:$album_title_color;
    margin-right: 12px;
    font-size: 18px;
    }
  }
}
</style>