<template>
  <div class="col-2  my-3">
    <img class="img-fluid" :src="`http://image.tmdb.org/t/p/w500/${detailsMovie.poster_path}`" alt="">
    <h5>Film</h5>
    <div class="pb-1"><strong>Titolo: </strong>{{detailsMovie.title}}</div>
    <div class="pb-1"><strong>Titolo originale: </strong>{{detailsMovie.original_title}}</div>
    <div class="pb-1">
        <strong>Voto: </strong>
        <font-awesome-icon icon="fa-solid fa-star" v-bind:class="(detailsMovie.vote_average / 2 > 0 || detailsMovie.vote_average == '')?'star':'star-empty'"/>
        <font-awesome-icon icon="fa-solid fa-star" v-bind:class="(detailsMovie.vote_average / 2 > 1 )?'star':'star-empty'"/>
        <font-awesome-icon icon="fa-solid fa-star" v-bind:class="(detailsMovie.vote_average / 2 > 2 )?'star':'star-empty'"/>
        <font-awesome-icon icon="fa-solid fa-star" v-bind:class="(detailsMovie.vote_average / 2 > 3 )?'star':'star-empty'"/>
        <font-awesome-icon icon="fa-solid fa-star" v-bind:class="(detailsMovie.vote_average / 2 > 4 )?'star':'star-empty'"/>
    </div>
    <div><strong>Lingua Originale: </strong>{{flagFunction()}}</div>
  </div>
</template>

<script>
export default {
    name: 'MoviesList',
    props:{
        detailsMovie: Object
    },
    data(){
        return{
            flag: '',
        }
    },
    methods: {
        flagFunction(){
            if ( this.detailsMovie.original_language == 'it' ){
                return this.flag = '🇮🇹'
            }
            else if( this.detailsMovie.original_language == 'en' ){
                return this.flag = '🇬🇧'
            }
            else{
                return this.flag = this.detailsMovie.original_language
            }
        }
    }
}
</script>

<style lang="scss" scoped>
    div{
        color: white;
        text-align: start;
        font-size: 0.8rem;
    }
    .star{
        color: yellow;
    }
    .star-empty{
        color: lightgrey;
    }
</style>