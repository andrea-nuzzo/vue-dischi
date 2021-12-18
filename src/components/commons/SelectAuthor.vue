<template>
  <div class="container">
      <div class="row">
          <div class="col">
            <select v-model= "author" class="form-select" aria-label="Default select example" @change="$emit('selectedAuthor', author)">
                <option value="">Select authors</option>
                <option v-for="(author, index) in allAuthors" :key="index" :value="author">{{author}}</option>
            </select>
          </div>
      </div>
  </div>
</template>

<script>
export default {
    name: 'SelectAuthor',

    props:{
        allAuthors: Array,
    },

    data(){
        return{
            author:'',
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