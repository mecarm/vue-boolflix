<template>
  <div class="col-1 mx3">
    <!-- <img class="img-fluid" :src="detailsMovie.backdrop_path" alt=""> -->
    <h3>{{detailsMovie.title}}</h3>
  </div>
</template>

<script>
export default {
    name: 'MoviesList',
    props:{
        detailsMovie: Object
    }
}
</script>

<style lang="scss" scoped>
    div{
        color: white;
    }
</style>