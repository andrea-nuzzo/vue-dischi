<template>
  <div class="container">
      <div class="row">
          <div class="col">
            <select v-model="genre" class="form-select" aria-label="Default select example" @change="$emit('selectedGenre', genre)">
                <option value="">Select musical genre</option>
                <option v-for="(genre, index) in allGenres" :key="index" :value="genre">{{genre}}</option>
            </select>
          </div>
      </div>
  </div>
</template>

<script>
export default {
    name: 'SelectGenre',

    props:{
        allGenres: Array,
    },

    data() {
        return{
            genre: '',
        }
    },
}
</script>

<style lang='scss' scoped>
select{
    background-color: black;
    color: rgb(85, 85, 85);
    border: 1px solid rgb(85, 85, 85);
}
</style>

