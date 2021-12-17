<template>
  <div>
    <SelectGenre class="mt-5" @selectedGenre="selectedGenre"/>
    <div class="container">
      <div class="row p-5 gy-4">
        <div class="col-12 col-sm-6 col-lg-4" v-for="(item, index) in genreFilter" :key="index">
          <AlbumCard :infoAlbum="item"/>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios'
import AlbumCard from '../commons/AlbumCard.vue'
import SelectGenre from '../commons/SelectGenre.vue'

export default {
    name: 'AlbumList',

    components: {
      AlbumCard,
      SelectGenre,
    },

  data(){
    return{
      dataAlbum: [],
      selected: "",
    }
  },

  methods:{
    selectedGenre(payload){
      this.selected = payload;
    },

    dataPresent(){
      console.log(this.genreFilter)
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

  computed: {
    genreFilter(){
      const arrayFiltered = this.dataAlbum.filter((item) => {
        return item.genre.includes(this.selected);
      });

      return arrayFiltered;
    }
  },
}
</script>

<style lang="scss" scoped>
</style>