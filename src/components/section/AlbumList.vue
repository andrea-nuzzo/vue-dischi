<template>
  <div>
    <SelectAuthor class="mt-3" @selectedAuthor="selectedAuthor" :allAuthors=" allAuthors"/>

    <SelectGenre class="mt-3" @selectedGenre="selectedGenre" :allGenres=" allGenres"/>

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
import SelectAuthor from '../commons/SelectAuthor.vue'

export default {
    name: 'AlbumList',

    components: {
      AlbumCard,
      SelectGenre,
      SelectAuthor,
    },

  data(){
    return{
      dataAlbum: [],
      selectedG: "",
      selectedA:"",
      allGenres: [],
      allAuthors: [],
    }
  },

  methods:{
    selectedGenre(payload){
      this.selectedG = payload;
      console.log(payload)
    },

    selectedAuthor(payload){
      this.selectedA = payload;
      console.log(payload)
    },


  },

  created(){
    axios.get('https://flynn.boolean.careers/exercises/api/array/music')
        .then((response) => {

          // Innesto in dataAlbum tutti gli oggetti dell'API
           this.dataAlbum = response.data.response

          //Ciclo per trovare tutti i generi e gli autori delle canzoni presenti in "dataAlbum"
           for(let i =0; i < this.dataAlbum.length; i++){

             //Trovo tutti i generi e li inserisco nell'array allGenres
            if(!this.allGenres.includes(this.dataAlbum[i].genre)){
              this.allGenres.push(this.dataAlbum[i].genre);
            }

            //Trovo tutti gli autori e li inserisco nell'array allGenres
            if(!this.allAuthors.includes(this.dataAlbum[i].author)){
              this.allAuthors.push(this.dataAlbum[i].author);
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
        return item.genre.includes(this.selectedG) && item.author.includes(this.selectedA);
      });
    }
  },
}
</script>

<style lang="scss" scoped>
</style>