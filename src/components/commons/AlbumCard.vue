<template>
  <div class='container card'>
    <div class="row">
      <div class="col">
        <img :src="infoAlbum.poster" :alt="`${infoAlbum.title}-${infoAlbum.author}`">
        <h3 class="text-uppercase fs-4">{{infoAlbum.title}}</h3>
        <p class="small">{{infoAlbum.author}}</p>
        <p class="small">{{infoAlbum.year}}</p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
    name: 'AlbumCard',
    props:{
        infoAlbum: Object,
    }
}

</script>


<style lang="scss" scoped>

  .card{
    height: 100%;
    background-color: #2e3a46;
    padding: 30px;

    img{
      width: 100%;
    }
    h3{
      margin-top: 20px ;
      color: white;
      font-weight: bold;
      text-align: center;
    }

    p{
      text-align: center;
      margin: 0;
      color: #808080;
    }

  }

</style>
