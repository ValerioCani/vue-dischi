<template>
    <main>
        <section>
            <albumCard  v-for="(album, index) in filterAlbums" :key="index" :details="album"/>
        </section>
    </main>
</template>

<script>
import axios from 'axios';
import albumCard from './albumCard.vue'

export default {
    name:'spotifyMain',
    props:{
       SentSelectedGenre:String 
    },
    components: {
        albumCard
    },
    data(){
        return{
            albumArray:[],
            genreArray:[]
        }
    },
    computed:{
        filterAlbums(){
                if(this.SentSelectedGenre==""){
                    return this.albumArray;
                } else{
                   return this.albumArray.filter(album => album.genre == this.SentSelectedGenre)
                }
        }
    },
    created(){
        axios.get('https://flynn.boolean.careers/exercises/api/array/music')
        .then(serverAnswer => {
            this.albumArray = serverAnswer.data.response;
            //da qui parte la creazione dell'array dei generi
            for( let i=0; i<this.albumArray.length; i++){
                if(!this.genreArray.includes(this.albumArray[i].genre)){
                    this.genreArray.push(this.albumArray[i].genre);
                }
            }
            this.$emit('ObtainGenres', this.genreArray)
        })
    }
} 
</script>

<style scoped lang="scss">
@import'../stylesheets/var.scss';
@import'../stylesheets/general.scss';
main{
background-color: $secondary_color;
height: 675px;
display: flex;
justify-content: center;
align-items: center;
    section{
    width: 900px;
    display: flex;
    flex-wrap: wrap;
    }
}
</style>