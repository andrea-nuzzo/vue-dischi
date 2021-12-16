<template>
  <header>
      <div class="row h-100 d-felx align-items-center ps-5">
        <div class="col">
          <img src="../../assets/img/package-lock.png" alt="">
        </div>
      </div>
  </header>
</template>

<script>
export default {
    name: 'Header',

}
</script>

<style lang="scss" scoped>
  header{
    background-color: #2e3a46;
    height: 80px;

    img{
      height: 40px;
    }
  }
</style>