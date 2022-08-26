<template>
  <header>
    <img src="../assets/logo-small.svg" alt="">
  </header>
</template>

<script>
export default {
    name:'spotifyHeader',
}
</script>

<style scoped lang="scss">
@import'../stylesheets/var.scss';
@import'../stylesheets/general.scss';
header{
height: 55px;
background-color: $primary_color;
  img{
  height: 100%;
  padding: 12px;
  }
}
</style>