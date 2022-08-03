<template>
    <main>
        <div class="container-elements">

            <div class="mt-5"> 
                <a v-show="searchedFilmList != 0"  class="anchor" href="#film-list">FILM</a>
                <a v-show="searchedSeriesList != 0" class="anchor" href="#series-list">SERIE TV</a>
            </div>
            
            <div class="pt-3" v-show="searchedFilmList == 0">
                <h2 class="text-white text-start display-2 text-center fw-bold">I <span class="main-text-color">FILM</span> DEL MOMENTO</h2>
                <ElementsList
                :searchedElements="trends"
                :searchedCast="searchedFilmActors"
                :genreList="movieGenre"
                />              
            </div>

            <div class="py-5" v-show="searchedFilmList != 0" id="film-list">
                <h2 class="text-white text-start display-2 text-center fw-bold">FILM</h2>
                <ElementsList
                :searchedElements="searchedFilmList"
                :searchedCast="searchedFilmActors"
                :genreList="movieGenre"
                />              
            </div>

            <div class="py-4" v-show="searchedSeriesList != 0" id="series-list">
                <h2 class="text-white text-start display-2 text-center fw-bold">SERIE TV</h2>
                 <ElementsList
                :searchedElements="searchedSeriesList"     
                :searchedCast ="searchedSeriesActors"
                :genreList="seriesGenre"
                />
            </div>
            
        </div>
    </main>
</template>

<script>
import axios from 'axios';
import ElementsList from "./ElementsList.vue"

export default {
 props:{
    searchedFilmList:Array,
    searchedSeriesList:Array,
    searchedFilmActors:Array,
    searchedSeriesActors:Array,
    keyApi:String,
    },
 components:{
    ElementsList,
 },
 data:function(){
    return{
        trends:[],
        seriesGenre:[],
        movieGenre:[],
    }
 },
 created(){
     axios.get(`https://api.themoviedb.org/3/trending/movie/day?api_key=${this.keyApi}`) // Facciamo una ricerca nei film e popoliamo il suo array
                .then( (result) => {   
                    this.trends = result.data.results
                    axios.get(`https://api.themoviedb.org/3/genre/movie/list?api_key=${this.keyApi}`)
                        .then((result) => {
                          this.movieGenre = result.data.genres
                        })
                       .catch((error) => {
                         console.warn(error)
                         })
                    })
                    axios.get(`https://api.themoviedb.org/3/genre/tv/list?api_key=${this.keyApi}`)
                        .then((result) => {
                          this.seriesGenre = result.data.genres
                        })    
                        .catch((error) => {
                         console.warn(error)
                         })   
                    .catch((error) => {
                        console.warn(error)
                        })
    }
}   
</script>

<style lang="scss">
@import "../styles/variables.scss";
// Style for both menu horizontal scroll
main{
    margin-top: 150px;
}
.container-elements{
    margin: 0 100px;

    .anchor{
        text-decoration: none;
        color: white;
        padding: 10px 15px;
        text-align: center;
        background-color: grey;
        border-radius: 10px;
        margin: 0 10px;
        letter-spacing: 2px;
    }
}

</style>
