<template>
  <div>
    <div class="container">
      <div class="row p-5 gy-4">
        <div class="col-12 col-sm-6 col-lg-4" v-for="(item, index) in dataAlbum" :key="index">
          <AlbumCard :infoAlbum="item"/>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios'
import AlbumCard from '../commons/AlbumCard.vue'


export default {
    name: 'AlbumList',
    components: {
      AlbumCard,
    },

  data(){
    return{
      dataAlbum: null,
    }
  },

  created(){

    axios.get('https://flynn.boolean.careers/exercises/api/array/music')
        .then((response) => {
            // handle success
           this.dataAlbum = response.data.response
        })
        .catch(function (error) {
            // handle error
            console.log(error);
        });
  },
}
</script>

<style lang="scss" scoped>

</style>
