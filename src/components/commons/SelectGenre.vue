<template>
  <div class="container">
      <div class="row">
          <div class="col">
            <select v-model="genre" class="form-select" aria-label="Default select example" @change="$emit('selectedGenre', genre)">
                <option value="">Select musical genre</option>
                <option value="Rock">Rock</option>
                <option value="Pop">Pop</option>
                <option value="Jazz">Jazz</option>
                <option value="Metal">Metal</option>
            </select>
          </div>
      </div>
  </div>
</template>

<script>
export default {
    name: 'SelectGenre',
    data() {
        return{
            genre: '',
        }
    }
}
</script>

<style lang='scss' scoped>
select{
    background-color: black;
    color: rgb(85, 85, 85);
    border: 1px solid rgb(85, 85, 85);
}
</style>

