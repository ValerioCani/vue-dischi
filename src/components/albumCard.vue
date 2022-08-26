<template>
    <div class="card">
        <img :src="details.poster" alt="">
        <h2>{{details.title}}</h2>
        <p>{{details.author}}</p>
        <p>{{details.year}}</p>
    </div>
</template>

<script>
export default {
    name: 'albumCard',
    props:{
        details:Object
    }
}
</script>

<style scoped lang="scss">
@import'../stylesheets/var.scss';
@import'../stylesheets/general.scss';
.card{
height: 270px;
width: 150px;
margin: 15px;
background-color: $primary_color;
padding: 13px;
text-align: center;
    img{
    width: 100%;
    }
    h2{
    color: $album_title_color;
    text-transform: uppercase;
    font-size: 20px;
    margin: 10px 0;
    }
    p{
    color: $album_text_color;
    font-size: 14px;
    }
}
</style>