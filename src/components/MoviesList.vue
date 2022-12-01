<template>
    <div class="col-md-2 col-sm-6 my-3">
        <img class="img-fluid" :src="`http://image.tmdb.org/t/p/w500/${detailsMovie.poster_path}`" alt="">
        <div class="d-none">
            <h5>Film</h5>
            <div class="pb-1"><strong>Titolo: </strong>{{detailsMovie.title}}</div>
            <div class="pb-1"><strong>Titolo originale: </strong>{{detailsMovie.original_title}}</div>
            <div class="pb-1 trama"><strong>Trama: </strong>{{detailsMovie.overview}}</div>
            <div class="pb-1">
                <strong>Voto: </strong>
                <font-awesome-icon icon="fa-solid fa-star"
                    v-bind:class="(detailsMovie.vote_average / 2 > 0 || detailsMovie.vote_average == '')?'star':'star-empty'" />
                <font-awesome-icon icon="fa-solid fa-star"
                    v-bind:class="(detailsMovie.vote_average / 2 > 1 )?'star':'star-empty'" />
                <font-awesome-icon icon="fa-solid fa-star"
                    v-bind:class="(detailsMovie.vote_average / 2 > 2 )?'star':'star-empty'" />
                <font-awesome-icon icon="fa-solid fa-star"
                    v-bind:class="(detailsMovie.vote_average / 2 > 3 )?'star':'star-empty'" />
                <font-awesome-icon icon="fa-solid fa-star"
                    v-bind:class="(detailsMovie.vote_average / 2 > 4 )?'star':'star-empty'" />
            </div>
            <div class="pb-1"><strong>Lingua Originale:  </strong><img class="flag" :src="flagFunction()" alt=""></div>
            <div><strong>Data di rilascio: </strong>{{detailsMovie.release_date}}</div>
            <div>{{functionComputed((detailsMovie.id))}}</div>
        </div>

    </div>
</template>

<script>
import axios from 'axios'

export default {
    name: 'MoviesList',
    props:{
        detailsMovie: Object
    },
    data(){
        return{
            arrayActors: [],
            actor: []
        }
    },
    methods: {
        flagFunction(){
            if ( this.detailsMovie.original_language == 'en' ){
                return "https://www.countryflagicons.com/SHINY/64/GB.png"
            }
            else if( this.detailsMovie.original_language == 'ja' ){
                return "https://www.countryflagicons.com/SHINY/64/JP.png"
            }
            else{
                return 'https://www.countryflagicons.com/SHINY/64/'+ this.detailsMovie.original_language.toUpperCase() +'.png'
            }
        },
        functionComputed(param) {
            
            axios.get('https://api.themoviedb.org/3/movie/'+param+'/credits?api_key=376598589f212a721599521e853baab1&language=it-IT#')
                .then((response)=>{
                    for ( let i = 0; i < 5; i++){
                        this.arrayActors = response.data.cast[i].name;
                        console.log(this.arrayActors)
                    }
                    
                })
                // for( let i = 0; i < 5; i++){
                //     // this.actor.push
                //     console.log(this.arrayActors[i].original_name)
                // }
                // console.log(this.actor)
                // this.actor = this.arrayActors.slice(0, 5)
                // console.log(this.actor)

            // ciclo for per estrarre i primi 5 nomi degli attori
            
        },
        // functionNameActor() {
        //     for (let i = 0; i < 5; i++) {
        //         // this.actor.push
        //         console.log(this.arrayActors[i].original_name)
        //     }
        // }
    
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