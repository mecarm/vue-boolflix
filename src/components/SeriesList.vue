<template>
    <div class="col-1 mx3">
      <!-- <img class="img-fluid" :src="detailsMovie.backdrop_path" alt=""> -->
      <h5>SERIE</h5>
      <div class="pb-1"><strong>Titolo: </strong>{{detailsSeries.name}}</div>
      <div class="pb-1"><strong>Titolo originale: </strong>{{detailsSeries.original_name}}</div>
      <div class="pb-1"><strong>Voto: </strong>{{detailsSeries.vote_average}}</div>
      <div><strong>Lingua Originale: </strong>{{flagFunction()}}</div>
    </div>
  </template>
  
  <script>
  export default {
      name: 'SeriesList',
      props:{
        detailsSeries: Object
      },
      data(){
          return{
              flag: ''
          }
      },
      methods: {
          flagFunction(){
              if ( this.detailsSeries.original_language == 'it' ){
                  return this.flag = '🇮🇹'
              }
              else if( this.detailsSeries.original_language == 'en' ){
                  return this.flag = '🇬🇧'
              }
              else{
                  return this.flag = this.detailsSeries.original_language
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
  </style>