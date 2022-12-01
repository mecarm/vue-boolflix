<template>
    <div class="col-md-2 col-sm-6 my-3">
        <img class="img-fluid" :src="`http://image.tmdb.org/t/p/w500/${detailsSeries.poster_path}`" alt="">
        <div class="d-none">
            <h5>SERIE</h5>
            <div class="pb-1"><strong>Titolo: </strong>{{detailsSeries.name}}</div>
            <div class="pb-1"><strong>Titolo originale: </strong>{{detailsSeries.original_name}}</div>
            <div class="pb-1 trama"><strong>Trama: </strong>{{detailsSeries.overview}}</div>
            <div class="pb-1">
                <strong>Voto: </strong>
                <font-awesome-icon icon="fa-solid fa-star"
                    :class="(detailsSeries.vote_average / 2 > 0 || detailsSeries.vote_average == '')?'star':'star-empty'" />
                <font-awesome-icon icon="fa-solid fa-star"
                    :class="(detailsSeries.vote_average / 2 > 1 )?'star':'star-empty'" />
                <font-awesome-icon icon="fa-solid fa-star"
                    :class="(detailsSeries.vote_average / 2 > 2 )?'star':'star-empty'" />
                <font-awesome-icon icon="fa-solid fa-star"
                    :class="(detailsSeries.vote_average / 2 > 3 )?'star':'star-empty'" />
                <font-awesome-icon icon="fa-solid fa-star"
                    :class="(detailsSeries.vote_average / 2 > 4 )?'star':'star-empty'" />
            </div>
            <div><strong>Lingua Originale:  </strong><img class="flag" :src="flagFunction()" alt=""></div>
            <div><strong>Data di rilascio: </strong>{{detailsSeries.release_date}}</div>
        </div>
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
            if ( this.detailsSeries.original_language == 'en' ){
                return "https://www.countryflagicons.com/SHINY/64/GB.png"
            }
            else if( this.detailsSeries.original_language == 'ja' ){
                return "https://www.countryflagicons.com/SHINY/64/JP.png"
            }
            else{
                return 'https://www.countryflagicons.com/SHINY/64/'+ this.detailsSeries.original_language.toUpperCase() +'.png'
            }
      }
  }
}
  </script>
  
<style lang="scss" scoped>
div {
    color: white;
    text-align: start;
    font-size: 0.8rem;
}

.star {
    color: yellow;
}

.star-empty {
    color: lightgrey;
}

.flag{
    width: 20px;
    height: 20px;
}

.col-md-2, .col-sm-6 {

    &:hover {
        border: 1px solid rgba(211, 211, 211, 0.187);

        .img-fluid {
            display: none;
        }

        .d-none {
            display: block !important;
            padding: 10px;

            .trama {
                max-height: 100px;
                overflow: auto;
            }

            .trama::-webkit-scrollbar-track {
                border: 1px solid #000;
                padding: 2px 0;
                background-color: #404040;
            }

            .trama::-webkit-scrollbar {
                width: 10px;
            }

            .trama::-webkit-scrollbar-thumb {
                border-radius: 10px;
                box-shadow: inset 0 0 6px rgba(0, 0, 0, .3);
                background-color: #737272;
                border: 1px solid #000;
            }
        }
    }
}
</style>