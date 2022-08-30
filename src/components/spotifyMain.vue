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
        SentSelectedGenre:String,
        SentSelectedArtist:String
        },
        components: {
            albumCard
        },
        data(){
            return{
                albumArray:[],
                artistArray:[],
                genreArray:[]
            }
        },
        computed:{
            filterAlbums(){
                if(this.SentSelectedGenre=="" && this.SentSelectedArtist==""){
                    return this.albumArray;
                } else if(this.SentSelectedGenre=="" && !this.SentSelectedArtist==""){
                    return this.albumArray.filter(album => album.author == this.SentSelectedArtist)
                } else if(!this.SentSelectedGenre=="" && this.SentSelectedArtist==""){
                    return this.albumArray.filter(album => album.genre == this.SentSelectedGenre)
                } else {
                    return this.albumArray.filter(album => album.genre == this.SentSelectedGenre).filter(album => album.author == this.SentSelectedArtist);
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

                for( let i=0; i<this.albumArray.length; i++){
                    if(!this.artistArray.includes(this.albumArray[i].author)){
                        this.artistArray.push(this.albumArray[i].author);
                    } 
                }
                this.$emit('ObtainGenres', this.genreArray)
                this.$emit('ObtainArtist', this.artistArray)
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