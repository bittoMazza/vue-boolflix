<template>
  <div id="app">
    <Header
    @selectElement="SearchElementsName"
    />
    <Main
    :searchedFilmList="searchedFilmList"
    :searchedSeriesList="searchedSeriesList"
    :searchedFilmActors="searchedFilmCast"
    :searchedSeriesActors="searchedSeriesCast"
    :keyApi="apiKey"
    />
  </div>
</template>

<script>
import Header from "./components/Header.vue"
import Main from "./components/Main.vue"
import axios from 'axios';


export default {
  name: 'App',
  components: {
    Header,
    Main
  },
  data:function(){
    return{
      searchedFilmList:[],
      searchedSeriesList:[],
      searchedFilmCast:[],
      searchedSeriesCast:[],
      apiKey:"f6a28c97150ef559daa0a8f32bc1fee9",
    }
  },
  methods:{
    SearchElementsName(Element){
            if(Element == null || Element == ''){
                alert('Inserisci il nome del film/serie da cercare')
            }
            else{
                 axios.get(`https://api.themoviedb.org/3/search/movie?api_key=${this.apiKey}&&language=it-IT&query=${Element}`) // Facciamo una ricerca nei film e popoliamo il suo array
                .then( (result) => {   
                        this.searchedFilmList = result.data.results
                        for(let i=0; i < this.searchedFilmList.length;i++){
                          axios.get(`https://api.themoviedb.org/3/movie/${this.searchedFilmList[i].id}/credits?api_key=f6a28c97150ef559daa0a8f32bc1fee9`)
                            .then( (result) => {   
                            this.searchedFilmCast.push(result.data.cast.slice(0,5))
                        }) 
                        }
                        })                   
                .catch((error) => {
                  console.warn(error)
                })
                axios.get(`https://api.themoviedb.org/3/search/tv?api_key=${this.apiKey}&&language=it-IT&query=${Element}`) // Facciamo una ricerca nelle serie e popoliamo il suo array
                .then( (result) => {   
                        this.searchedSeriesList = result.data.results                  
                          for(let i=0; i < this.searchedSeriesList.length;i++){
                          axios.get(`https://api.themoviedb.org/3/tv/${this.searchedSeriesList[i].id}/credits?api_key=f6a28c97150ef559daa0a8f32bc1fee9`)
                            .then( (result) => {   
                            this.searchedSeriesCast.push(result.data.cast.slice(0,5))
                            })
                        }
                           console.log(this.searchedSeriesCast)
                        })                   
                    .catch((error) => {
                        console.warn(error)
                    })
            }
           
        },
  },
 
}
</script>

<style lang="scss">
@import "./styles/variables.scss";
@import "~bootstrap-icons/font/bootstrap-icons.css"; 
@import "~bootstrap/scss/bootstrap.scss";
body{
  background-color: $mainBg;
}
</style>
