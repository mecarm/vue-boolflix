<template>
  <div class="col-1 mx3">
    <!-- <img class="img-fluid" :src="detailsMovie.backdrop_path" alt=""> -->
    <div class="pb-1"><strong>Titolo: </strong>{{detailsMovie.title}}</div>
    <div class="pb-1"><strong>Titolo originale: </strong>{{detailsMovie.original_title}}</div>
    <div><strong>Voto: </strong>{{detailsMovie.vote_average}}</div>
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
        text-align: start;
        font-size: 0.8rem;
    }
</style>