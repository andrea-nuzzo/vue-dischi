<template>
  <div>
    <SelectGenre class="mt-5" @selectedGenre="selectedGenre" :allGenres=" allGenres"/>
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
      allGenres: [],
    }
  },

  methods:{
    selectedGenre(payload){
      this.selected = payload;
    },

    dataPresent(){
      console.log(this.genreFilter)
    },
  },

  created(){
    axios.get('https://flynn.boolean.careers/exercises/api/array/music')
        .then((response) => {

          // Innesto in dataAlbum tutti gli oggetti dell'API
           this.dataAlbum = response.data.response

          //Ciclo per trovare tutti i generi delle canzoni presenti in "dataAlbum"
           for(let i =0; i < this.dataAlbum.length; i++){
            if(!this.allGenres.includes(this.dataAlbum[i].genre)){
              this.allGenres.push(this.dataAlbum[i].genre);
            }
          }

        })
        .catch(function (error) {
            // handle error
            console.log(error);
        });
  },


  computed: {
    //Funzione che filtra sui generi di musica
    genreFilter(){
      return this.dataAlbum.filter((item) => {
        return item.genre.includes(this.selected);
      });
    }
  },
}
</script>

<style lang="scss" scoped>
</style>