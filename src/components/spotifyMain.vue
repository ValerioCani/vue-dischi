<template>
    <main>
        <section>
            <albumCard v-for="(album, index) in albumArray" :key="index" :details="album"/>
        </section>
    </main>
</template>

<script>
import axios from 'axios';
import albumCard from './albumCard.vue'

export default {
    name:'spotifyMain',
    components: {
    albumCard
    },
    data(){
        return{
            albumArray:[]
        }
    },
    created(){
        axios.get('https://flynn.boolean.careers/exercises/api/array/music')
        .then(response => {
            this.albumArray = response.data.response;
            console.log(this.albumArray);
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